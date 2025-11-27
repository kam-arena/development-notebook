# Prompts para GitHub Copilot

## ¿Qué es un prompt?

Un *prompt* es una instrucción o pregunta que se le proporciona a GitHub Copilot para guiar la generación de código, documentación o sugerencias. Un buen prompt ayuda a obtener resultados más precisos y útiles.

## Buenas prácticas para crear prompts

- **Sé claro y específico:** Explica exactamente lo que necesitas. Por ejemplo, en vez de pedir "haz una función", indica el propósito y los parámetros.
- **Incluye contexto:** Si es relevante, proporciona fragmentos de código, estructuras de datos o ejemplos de entrada/salida.
- **Utiliza lenguaje natural:** Escribe los prompts como si explicaras a otra persona, evitando ambigüedades.
- **Divide tareas complejas:** Si la tarea es extensa, divídela en pasos o solicita partes específicas.
- **Revisa y ajusta:** Si el resultado no es el esperado, reformula el prompt para ser más claro o detallado.


## Ejemplos de prompts

### Ejemplo 1: Solicitud de función simple

```markdown
Crea una función en JavaScript que reciba un array de números y devuelva la suma de sus elementos.
```

### Ejemplo 2: Solicitud con contexto

```markdown
Tengo la siguiente clase en Python:

class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

Agrega un método que devuelva si la persona es mayor de edad.
```

### Ejemplo 3: Solicitud de documentación

```markdown
Genera la documentación en formato Markdown para la función sumar_numeros(a, b) que retorna la suma de dos números.
```

## Consejos adicionales

- Utiliza ejemplos de entrada y salida para clarificar el comportamiento esperado.
- Si necesitas un estilo de codificación específico, indícalo en el prompt.
- Para obtener explicaciones, pide que se incluyan comentarios en el código generado.
