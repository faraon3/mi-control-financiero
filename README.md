# Mi Control Financiero

Aplicación Android offline para organizar finanzas personales, gastos compartidos, deudas y planificación de sueldo.

## Contenido
- `www/index.html`: interfaz y lógica de la aplicación.
- `package.json` y `capacitor.config.json`: configuración de Capacitor.
- `.github/workflows/build-apk.yml`: compila APK debug y, si se configuran secretos de firma, APK release firmado.
- `.github/workflows/validate-app.yml`: valida estructura, sintaxis y dependencias en cada solicitud de cambios.

## Compilar y probar
1. Abre **Actions** en GitHub.
2. Ejecuta **Construir APK Android** o revisa el flujo iniciado por una solicitud de cambios.
3. Descarga el artefacto `mi-control-financiero-apk-debug` para pruebas.
4. No reemplaces la instalación que contiene tus datos hasta exportar una copia JSON o una copia cifrada y probar la restauración.

## APK release firmado
Para generar un APK que pueda actualizarse de forma estable, configura en **Settings → Secrets and variables → Actions** los secretos:
- `ANDROID_KEYSTORE_BASE64`: archivo keystore codificado en Base64.
- `ANDROID_KEYSTORE_PASSWORD`: contraseña del keystore.
- `ANDROID_KEY_ALIAS`: alias de la llave.
- `ANDROID_KEY_PASSWORD`: contraseña de la llave.

Con los cuatro secretos presentes, el flujo firma y verifica el APK release. Sin ellos, solo publica el APK debug de prueba. Guarda el keystore y sus contraseñas en un lugar seguro; si se pierde la llave, no se podrá firmar una actualización compatible con la instalación firmada con ella.

## Funciones añadidas en esta tanda
- Gastos del hogar con reparto mitad y mitad, una persona asume todo o importes personalizados en COP.
- Registro de quién pagó, saldo entre ambos y liquidación de transferencias.
- Copia de seguridad cifrada con contraseña AES-GCM y opción de restauración cifrada.
- Importación guiada de movimientos desde CSV bancario con detección de columnas comunes y omisión de duplicados simples.
- Ingresos y gastos recurrentes semanal, quincenal, mensual o anual; las ocurrencias se generan cuando se abre la app después de su fecha.
- Recordatorios locales de facturas y deudas en Android, con permiso explícito del dispositivo.
- Corrección del cálculo de cuotas cubiertas cuando un abono paga más de una cuota.
- Correcciones en proyección de informes y actualización de fecha al volver a la app.

## Límites y advertencias
La app sigue siendo offline y no se conecta a bancos ni ejecuta pagos. Las notificaciones requieren la APK Android actualizada y permiso del sistema; la versión web no puede garantizar recordatorios en segundo plano. La copia cifrada depende de que recuerdes su contraseña. El APK debug es solo para pruebas. Aún deben completarse pruebas de extremo a extremo, revisar la migración a almacenamiento más robusto y evaluar PIN/biometría antes de considerar la app lista para datos financieros sensibles.
