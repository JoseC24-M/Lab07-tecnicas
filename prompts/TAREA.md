# Tarea: Mi prompt avanzado

## Tarea elegida
Generación de casos de prueba unitarios e implementación en JUnit 5 para una clase de gestión de productos Java (`producto.java`).

---

## Version 1: prompt basico

Crea pruebas para la clase producto.java en Java.

## Version 2
Actúa como un QA Automation Engineer especializado en Java y JUnit 5.
Vas a generar pruebas unitarias para la clase producto.java dividiendo el trabajo en los siguientes pasos:
1. Revisa la clase e identifica las entradas válidas e inválidas.
2. Genera los métodos de prueba usando JUnit 5 y AssertJ.
3. Devuelve los casos de prueba organizados en una tabla explicativa y luego el código Java.

## Version 3 
[ROL]
Actúa como un QA Automation Engineer Senior especializado en pruebas unitarias para Java y JUnit 5.

[DESCOMPOSICIÓN DE TAREAS]
Realiza las siguientes tareas en secuencia sobre la clase producto.java:
1. Analiza los atributos principales de la clase (id, nombre, precio, stock).
2. Razona sobre los escenarios límite (precios negativos, stock cero, nombres vacíos o nulos).
3. Construye una tabla resumen con los casos de prueba.
4. Escribe el código de las pruebas unitarias en JUnit 5.

[CHAIN OF THOUGHT]
Antes de dar el código final, explica paso a paso tu razonamiento sobre qué casos de prueba frontera son críticos para esta entidad y por qué los seleccionaste.

[ONE-SHOT / FEW-SHOT]
Sigue este formato estándar de ejemplo para la definición de cada método de prueba en el código final:

@Test
@DisplayName("Debe lanzar IllegalArgumentException cuando el precio es negativo")
void testPrecioNegativo() {
    // 1. Arrange
    Producto p = new Producto();
    
    // 2. Act & Assert
    assertThrows(IllegalArgumentException.class, () -> p.setPrecio(-10.0));
}

[FORMATO DE RESPUESTA]
Tu respuesta debe estructurarse estrictamente así:
1. Seccion "Razonamiento de casos límite" (Chain of Thought).
2. Tabla Markdown con columnas: ID, Descripción del Caso, Entrada, Resultado Esperado.
3. Bloque de código Java compilable utilizando anotaciones de JUnit 5 (@Test, @DisplayName).


## Tecnicas usadas en el prompt final

| Sección del Prompt Final | Técnica Aplicada |
| :--- | :--- |
| `[ROL] Actúa como un QA Automation Engineer Senior...` | Role Prompting |
| `[DESCOMPOSICIÓN DE TAREAS] Realiza las siguientes tareas...` | Descomposición de tareas |
| `[CHAIN OF THOUGHT] Antes de dar el código final, explica paso a paso...` | Chain of Thought (CoT) |
| `[ONE-SHOT / FEW-SHOT] Sigue este formato estándar de ejemplo...` | One-Shot / Few-Shot |
| `[FORMATO DE RESPUESTA] Tu respuesta debe estructurarse...` | Prompt Estructurado |

## Evaluacion del resultado

| Criterio de Evaluación | Cumplido (Sí / No) | Observaciones |
| :--- | :---: | :--- |
| ¿Asume un rol específico que no es "experto"? | **Sí** | Se especificó "QA Automation Engineer Senior especializado en Java y JUnit 5". |
| ¿Solicita explícitamente un razonamiento paso a paso? | **Sí** | La sección Chain of Thought exige explicar los casos límite antes de mostrar el código. |
| ¿Incluye al menos un ejemplo de formato esperado (One-Shot)? | **Sí** | Se provee la estructura exacta del método JUnit con comentarios Arrange-Act-Assert. |
| ¿Define un formato claro para la respuesta final? | **Sí** | Exige 3 secciones delimitadas (Razonamiento, Tabla Markdown y Código Java). |

## Por que elegi estas tecnicas
Elegí Role Prompting, Descomposición, Chain of Thought y One-Shot porque en la generación de pruebas de software los modelos de lenguaje tienden a crear únicamente los casos triviales (casos de éxito o "happy path"). Al asignar un rol de QA Automation Engineer, el modelo adopta un enfoque analítico enfocado en la prevención de fallos. La descomposición y el Chain of Thought obligan a evaluar primero las reglas de negocio y escenarios de borde (como precios negativos o nulos) antes de codificar. Por último, la técnica One-Shot garantiza que el código producido cumpla estrictamente las convenciones de nomenclatura y estructura estandarizadas del proyecto.

