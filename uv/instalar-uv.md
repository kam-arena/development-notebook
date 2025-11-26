# Instalación y configuración de `uv`

[Inicio](init-uv.md) > [`uv`](../init.md)

---

`uv` es una herramienta de Astral para gestionar entornos y dependencias de Python con un enfoque rápido y reproducible.

## Requisitos previos

- PowerShell 5.1 o superior (o PowerShell 7) con acceso a Internet.
- Permisos para añadir carpetas al `PATH` del usuario.

## Instalación

### Windows (PowerShell)

1. Abre PowerShell (puede ser una sesión normal, no requiere modo administrador).
2. Ejecuta el instalador oficial:

   ```powershell
   irm https://astral.sh/uv/install.ps1 | iex
   ```

3. Reinicia la terminal o ejecuta `refreshenv` (si usas Windows Terminal/Chocolatey) para que la nueva ruta quede disponible.

### macOS y Linux (bash/zsh)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Verificar la instalación

```powershell
uv --version
```

Si el comando responde con la versión instalada, `uv` quedó registrado correctamente en el `PATH`. En Windows la ruta por defecto es `%USERPROFILE%\.local\bin`.

## Configuración inicial recomendada

- **Actualizar a la última versión disponible:**

  ```powershell
  uv self update
  ```

- **Instalar un intérprete de Python administrado por `uv` (ejemplo: 3.12):**

  ```powershell
  uv python install 3.12
  ```

  Esto crea un runtime aislado en la caché de `uv` y evita depender de instalaciones globales de Python.

- **Habilitar autocompletado en PowerShell:**

  ```powershell
  $profilePath = "$env:USERPROFILE\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
  if (-not (Test-Path $profilePath)) { New-Item -ItemType File -Path $profilePath | Out-Null }
  uv generate-shell-completion powershell | Out-File -FilePath $profilePath -Append
  ```

  Cierra y vuelve a abrir PowerShell para cargar las nuevas completaciones.

- **Crear un proyecto base:**

  ```powershell
  mkdir mi-proyecto-uv
  Set-Location mi-proyecto-uv
  uv init
  ```

  El comando genera un `pyproject.toml`, crea un entorno virtual administrado por `uv` y deja todo listo para instalar dependencias con `uv add <paquete>`.

## Recursos útiles

- Documentación oficial: <https://docs.astral.sh/uv/>
- Comandos disponibles: `uv --help`
- Configuración avanzada (`config.toml`): `uv config --help`