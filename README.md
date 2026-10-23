# Mi Control Financiero — proyecto inicial

Aplicación Android offline para organizar finanzas personales, gastos compartidos, deudas y planificación de sueldo.

## Contenido
- `www/index.html`: interfaz y lógica inicial del prototipo.
- `package.json` y `capacitor.config.json`: configuración de Capacitor.
- `.github/workflows/build-apk.yml`: flujo de GitHub Actions para compilar un APK de depuración.

## Cómo compilar
1. Crea un repositorio GitHub vacío y sube el contenido de este ZIP a la rama `main`.
2. En GitHub, abre **Actions** y habilita los flujos si te lo solicita.
3. Ejecuta **Construir APK Android** con **Run workflow**, o espera a que termine el flujo tras subir los archivos.
4. Cuando el flujo termine correctamente, entra al resultado y descarga el artefacto `Mi-Control-Financiero-APK`.
5. Descomprime el ZIP del artefacto y encontrarás `app-debug.apk`.

## Estado y advertencias
Este es un prototipo inicial funcional, no una versión financiera final auditada. Los datos se guardan en el almacenamiento local del WebView. No hay cifrado de base de datos, bloqueo PIN/biometría ni notificaciones locales implementadas todavía. El respaldo JSON no está cifrado. No sincroniza cuentas bancarias ni ejecuta pagos.

Antes de usarlo con datos reales, hay que probar y mejorar los cálculos de saldo por cuenta, la conciliación de gastos compartidos, el registro de abonos de deuda y el motor de prioridades. La app no sustituye el contrato, estado de cuenta ni información oficial de los acreedores.
