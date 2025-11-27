# Creando un buen archivo `copilot-instructions.md`

El archivo `copilot-instructions.md` debe incluir directrices claras y específicas para que GitHub Copilot pueda generar sugerencias relevantes y alineadas con las necesidades del proyecto. Aquí hay algunos consejos para crearlo:

1. **Descripción del proyecto**:  
   Explica brevemente el propósito del proyecto y el tipo de código que se espera generar.

2. **Estilo de codificación**:  
   Incluye detalles sobre las convenciones de codificación, como el uso de espacios o tabulaciones, el estilo de nombres de variables y funciones, y otros estándares.

3. **Ejemplos de código**:  
   Proporciona ejemplos de código que sirvan como referencia para las sugerencias de Copilot.

4. **Áreas de enfoque**:  
   Especifica las áreas donde Copilot debería centrarse, como generación de pruebas, documentación o implementación de funciones específicas.

5. **Restricciones**:  
   Define qué tipo de código no debe sugerir Copilot, como bibliotecas específicas que no se deben usar o patrones de diseño que se deben evitar.

## Ejemplo de `copilot-instructions.md`

```markdown
# copilot-instructions.md

## Descripción del proyecto
Este proyecto es una API REST para la gestión de tareas. Está desarrollado en Node.js con Express y utiliza una base de datos MongoDB.

## Estilo de codificación
- Usa 2 espacios para la indentación.
- Nombres de variables y funciones en camelCase.
- Sigue el estándar de JavaScript ES6+.

## Ejemplos de código
// Ejemplo de una ruta en Express
app.get('/tasks', async (req, res) => {
  const tasks = await Task.find();
  res.json(tasks);
});
```
