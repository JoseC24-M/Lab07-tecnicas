# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting.
Herramienta de IA usada: (escribe aqui cual usaste)

## Ejercicio 2: Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|--------------------------|
| Zero-shot | 5 | Lista con respuestas | Si |
| One-shot | 5| Lista que sigue el ejemplo | Si |
| Few-shot | 5 | Una lista que sigue el ejemplo pero con texto->etiqueta | Si |


## Ejercicio 3: Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|--------------|
| Directo | 318.60 | No | Si |
| Paso a paso | explicacion y resultado 318.60 | Si | Si |


## Ejercicio 4: Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|-------------------------------|-----------------------|----------------------|
| A. Sin rol | Sencillo | Si | a un estudiante |
| B. Rol docente | Sencillo | Si | a un estudiante con base |
| C. Rol senior | Tecnico | Si | A un desarrollador |


## Ejercicio 5: Descomposicion


1. Se creó un sistema de inventario en Java para una tienda.  
   **Comparación:** Cumple con el pedido inicial de crear el sistema.

2. Se definieron los requisitos principales: registrar productos, consultar productos, actualizar stock, controlar el stock y registrar movimientos.  
   **Comparación:** Cumple con las funciones principales solicitadas para el sistema.

3. Se diseñaron las clases `Producto`, `Inventario`, `Movimiento`, `SistemaInventario` y `Main`, incluyendo sus atributos y tipos de datos.  
   **Comparación:** Cumple con el diseño de las clases necesarias para organizar el sistema.

4. Se creó la clase `Producto` con sus atributos, constructor, métodos `get` y `set`.  
   **Comparación:** Cumple directamente con el pedido de implementar la clase `Producto`.

5. Se propusieron mejoras para la clase `Producto`: validar los datos, evitar valores negativos y agregar el método `toString()`.  
   **Comparación:** Mejora la seguridad, validación y visualización de los datos del producto.

6. Se revisó el resultado final y se comprobó que el sistema permite gestionar productos y controlar el inventario.  
   **Comparación:** El resultado cumple con el objetivo inicial de crear un sistema de inventario para una tienda.

## Ejercicio 6: Prompt estructurado y autocritica

| Qué revisar | Cumple (Sí / No) |
| :--- | :---: |
| ¿Tiene las 4 columnas pedidas? | Si |
| ¿Incluye el bloqueo después de 3 intentos? | Si |
| ¿Incluye casos con campos vacíos? | Si |
| ¿Indica qué casos agregó en la autocrítica? | Si |
| ¿Hay algún caso repetido o que no tenga sentido? | Si |

```text
(pega aqui tu prompt estructurado y el mensaje de autocritica)
```
Revisa tu tabla: faltan casos limite como campos vacios, correo sin @

  o contrasena con espacios? Agrega los que falten e indica cuales agregaste.    

Sí. Faltaban casos de validación de datos de entrada. Los agregaría para comprobar que el sistema no cuente como intento fallido una entrada que ni siquiera cumple el formato esperado.

| ID | Escenario | Datos de entrada | Resultado esperado |
| :--- | :--- | :--- | :--- |
| CP-01 | Inicio de sesión con credenciales correctas | Correo: usuario@email.com / Contraseña: Clave123 | El usuario inicia sesión correctamente. |
| CP-02 | Contraseña incorrecta | Correo: usuario@email.com / Contraseña: incorrecta | Se rechaza el acceso y se registra 1 intento fallido. |
| CP-03 | Segundo intento incorrecto | Correo: usuario@email.com / Contraseña: incorrecta2 | Se rechaza el acceso y se registran 2 intentos fallidos. |
| CP-04 | Tercer intento incorrecto | Correo: usuario@email.com / Contraseña: incorrecta3 | Se rechaza el acceso y la cuenta queda bloqueada. |
| CP-05 | Intento de acceso con cuenta bloqueada | Cuenta bloqueada / Contraseña correcta | No se permite el acceso y se informa que la cuenta está bloqueada. |
| CP-06 | Credenciales correctas antes del tercer intento | 2 intentos incorrectos + correo y contraseña correctos | Se permite el acceso y la cuenta no se bloquea. |
| CP-07 | Campos vacíos | Correo: vacío / Contraseña: vacío | Se solicita completar los campos. No se registra como intento fallido. |
| CP-08 | Correo sin @ | Correo: usuarioemail.com / Contraseña: Clave123 | Se muestra un error de formato de correo. No se registra como intento fallido. |
| CP-09 | Correo sin dominio | Correo: usuario@ / Contraseña: Clave123 | Se muestra un error de formato de correo. No se registra como intento fallido. |
| CP-10 | Contraseña con espacios | Correo: usuario@email.com / Contraseña: Clave 123 | El sistema valida la contraseña según las reglas definidas; si los espacios no están permitidos, muestra un error. |
| CP-11 | Correo con espacios | Correo: usuario @email.com / Contraseña: Clave123 | Se rechaza el formato del correo y no se registra como intento fallido. |
| CP-12 | Límite de 3 intentos | 3 contraseñas incorrectas consecutivas | La cuenta se bloquea exactamente después del tercer intento fallido, no antes. |

