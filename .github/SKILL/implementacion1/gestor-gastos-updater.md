gestor-gastos-updater
Implementa nuevos requerimientos (fecha obligatoria, image picker para facturas, editar, eliminar y ordenar) en la app Gestor de Gastos.

Instructions
Gestor Gastos Updater
Esta skill asiste en la implementación de las nuevas funcionalidades para el proyecto "Gestor de Gastos para Poliestudiantes" basado en Expo, SQLite y TypeScript.

When to Use
Cuando el usuario necesite añadir fecha obligatoria o soporte para adjuntar fotos de facturas.
Para habilitar la edición y eliminación de gastos.
Para agregar filtros de ordenamiento por monto.
Steps
Actualizar Esquema: Agrega invoice_uri a src/types/expense.ts y a la instrucción CREATE TABLE en src/database/database.ts.
Actualizar Repositorio: Añade funciones UPDATE y DELETE en src/database/expenseRepository.ts. Asegúrate de que insertExpense y getAllExpenses manejen invoice_uri.
Ampliar Contexto: Expón updateExpense y deleteExpense en ExpenseContext.tsx. Añade un método o estado para ordenar la lista de mayor a menor (b.amount - a.amount).
Dependencias e Interfaz: Instala expo-image-picker y @react-native-community/datetimepicker. Intégralos en AddExpenseModal.tsx para solicitar fecha y mostrar opciones de "Tomar foto" / "Subir de galería".
Actualizar Vistas: En ExpenseItem.tsx añade los controles (botones o swipe) de editar/eliminar y un indicador si el gasto contiene factura. En index.tsx añade un control (botón/switch) para ordenar.
Gotchas
Asegúrate de solicitar y manejar permisos de cámara y galería antes de llamar a ImagePicker.
Las URLs devueltas por Expo Image Picker son URIs locales (file://); guárdalas como TEXT en la BD.
Si alteras la tabla en SQLite (database.ts), recuerda en desarrollo borrar la caché o reinstalar la app para que la nueva tabla se cree correctamente (o implementa una migración ALTER TABLE).