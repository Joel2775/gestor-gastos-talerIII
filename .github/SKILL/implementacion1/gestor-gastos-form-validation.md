gestor-gastos-form-validation
Implementa validaciones profesionales en los formularios de gastos (control de monto con 2 decimales, obligatoriedad de categorías y sanitización alfanumérica de descripción).

Instructions
Gestor Gastos Form Validation
Esta skill asiste en la implementación de controles estrictos y validaciones de datos en los formularios (crear/editar) del proyecto "Gestor de Gastos para Poliestudiantes" en React Native.

When to Use
Cuando se requiera aplicar reglas de validación en la entrada de datos (inputs) del usuario.
Para sanitizar campos de texto o prevenir la entrada de caracteres especiales.
Para manejar estados de error y alertas de campos obligatorios en el envío del formulario.
Steps
Control del Campo Monto (Obligatorio y Numérico):

Asegurar que el TextInput use keyboardType="decimal-pad".
En el onChangeText, aplicar una expresión regular para permitir solo números y un máximo de dos decimales: ej. const regex = /^\d*\.?\d{0,2}$/.
En la función de guardado (handleSubmit), verificar que el valor sea mayor a 0 y no esté vacío.
Validación de Categoría (Obligatoria):

En el handleSubmit, evaluar si el estado category es null o vacío.
Si no hay categoría, bloquear el guardado y mostrar un mensaje de error visible al usuario (usando Alert.alert de React Native o un texto de error debajo del selector).
Control del Campo Descripción (Opcional, Alfanumérico, Máx 400 chars):

Añadir la propiedad maxLength={400} al TextInput de la descripción.
En el evento onChangeText, usar una expresión regular para filtrar caracteres especiales permitiendo solo letras, números y espacios: ej. const sanitizedText = text.replace(/[^a-zA-Z0-9\s]/g, '').
Actualizar el estado únicamente con el texto sanitizado.
Gotchas
El teclado decimal-pad en Android e iOS difiere a veces en cómo maneja las comas (,) vs los puntos (.). Asegúrate de reemplazar las comas por puntos antes de la validación regex.
Las validaciones en tiempo real (mientras el usuario escribe) dan mejor experiencia de usuario, pero siempre deben ir acompañadas de una validación final en la función de guardado (antes de interactuar con SQLite).