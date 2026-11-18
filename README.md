# Juana Star World ⭐ — Primera versión

Web app mobile-first de misiones y recompensas. Solo el nombre de Juana aparece antes del inicio de sesión. **No subir datos personales al repositorio.**

## Publicación

1. Crear repositorio **público** `juana` en la cuenta GitHub `oscarmartell`.
2. Subir `index.html`, `firebase-config.js`, `manifest.webmanifest` y opcionalmente este README y `firestore.rules.example` a la raíz.
3. GitHub → Settings → Pages → Deploy from branch → main / root → Save.
4. URL prevista: https://oscarmartell.github.io/juana/

## Configuración de acceso privado en Firebase

1. Crear proyecto Firebase gratuito (Spark), registrar una Web App, activar Authentication → Email/Password y Cloud Firestore.
2. En Firebase Authentication, crear dos usuarios **solo para la familia** (adulto y Juana); evitar publicar los correos y contraseñas. Usar correos bajo control del adulto y revisar las condiciones de edad/consentimiento aplicables.
3. Crear en Firestore, mediante la consola, los documentos `access/UID_DEL_ADULTO` con campo `role` string `admin` y `access/UID_DE_JUANA` con `role` string `child`.
4. Copiar las reglas de `firestore.rules.example` a Firestore → Rules → Publish. No funcionan hasta hacerlo.
5. En Authentication → Settings → Authorized domains, autorizar `oscarmartell.github.io`.
6. Colocar la **configuración pública** de Firebase en `firebase-config.js`. No introducir cuentas, contraseñas ni credenciales de servicio.
7. Crear misiones y recompensas desde el panel Familia. Una vez configurado, Juana podrá marcar misiones y solicitar premios.

**Nota de seguridad y versión:** Esta versión inicial es un MVP. La autorización de acceso a los datos se aplica en las reglas de Firestore; GitHub Pages no brinda privacidad al código fuente. Para robustecer la economía de estrellas y evitar abusos (por ejemplo, falsificar la puntuación o solicitar múltiples canjes), la próxima versión debe validar cada acreditación y canje en un backend o Cloud Functions transaccional. Hasta entonces, usar con supervisión familiar y no asociar dinero real automáticamente.

**Nota funcional:** Los datos se guardan en Firestore solo tras completar la configuración. Sin ella, la web muestra únicamente la portada pública. La sección «A mejorar» es orientativa y compara los últimos siete días; se perfeccionará para gestionar días sin clases y rutinas programadas. Los límites diarios se aplican en la interfaz, no todavía como política inviolable de servidor.