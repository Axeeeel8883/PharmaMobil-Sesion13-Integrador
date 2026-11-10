# Sesión 14 — guía de instalación, firma y checklist de entrega

Proyecto: PharmaMobil. **Estado: documento de preparación, no evidencia de builds ejecutados.**

## 1. Requisitos
Android Studio y JDK del proyecto, SDK de Android, proyecto KMP completo compilable, backend PharmaSoft accesible desde el teléfono, y dos teléfonos Android físicos de versiones o marcas diferentes. En iOS se necesita macOS y Xcode.

> Importante: `10.0.2.2` solo funciona en el emulador Android; en celular real se debe configurar la IP LAN del backend y la conectividad correspondiente.

## 2. Claves de firma Android
Crear el almacén de claves **fuera** del repositorio, mediante `keytool` instalado con el JDK. Ejemplo para Windows PowerShell (ajustar ruta personal):
```powershell
keytool -genkeypair -v -keystore "$env:USERPROFILE\pharmamobil-release.jks" -storetype JKS -keyalg RSA -keysize 2048 -validity 10000 -alias pharmamobil
```
Guardar clave, alias y contraseñas en un sitio privado seguro, y hacer copia de respaldo fuera del único equipo. No publicar el archivo ni las contraseñas.

Crear localmente `keystore.properties` en la raíz, nunca subirlo:
```properties
storeFile=C:/Users/TU_USUARIO/pharmamobil-release.jks
storePassword=REEMPLAZAR_SOLO_EN_LOCAL
keyAlias=pharmamobil
keyPassword=REEMPLAZAR_SOLO_EN_LOCAL
```
El archivo `.gitignore` excluye `keystore.properties`, `*.jks` y `*.keystore`.

## 3. Compilación pendiente de comprobar
Cuando se integre el proyecto KMP completo, identificar el nombre **real** del módulo Android y configurar en su `build.gradle.kts` la firma release, `versionCode=1`, `versionName="1.0.0"` y un `applicationId` definitivo. La guía docente usa `androidApp`, pero el proyecto real podría usar `composeApp`. No asumir cuál sin verlo.

En Windows, usar `gradlew.bat` en lugar de `./gradlew`. Si el módulo fuera `androidApp`, ejecutar:
```powershell
.\gradlew.bat :androidApp:bundleRelease
.\gradlew.bat :androidApp:assembleRelease
```
Verificar el APK generado con `apksigner verify --print-certs RUTA_DEL_APK`. Registrar la huella sin mostrar secretos. Un `.aab` no se instala directamente; instalar el `.apk` release en los teléfonos y probarlo independientemente de Android Studio.

Si la minificación ocasiona fallos de serialización/inyección, investigar las reglas R8/ProGuard y compilar de nuevo; documentar cualquier decisión de desactivarla.

## 4. Prueba en dispositivos físicos
En cada teléfono realizar las siguientes pruebas. Escribir **resultado real**, no marcar sin verificar.

| N.º | Prueba | Dispositivo 1 | Dispositivo 2 | Evidencia |
|---|---|---|---|---|
| 1 | Instalar APK firmado desde archivo | Pendiente | Pendiente | |
| 2 | Login correcto e incorrecto | Pendiente | Pendiente | |
| 3 | CRUD con validación fallida | Pendiente | Pendiente | |
| 4 | Acceso sin privilegio | Pendiente | Pendiente | |
| 5 | Abrir, leer y crear en modo avión | Pendiente | Pendiente | |
| 6 | Reconectar y sincronizar sin duplicación | Pendiente | Pendiente | |
| 7 | Permiso concedido/denegado/permanente | Pendiente | Pendiente | |
| 8 | Cerrar sesión y reabrir; token borrado | Pendiente | Pendiente | |

### Registro de defectos
| ID | Teléfono y Android | Pasos reproducibles | Esperado | Obtenido | Severidad | Estado |
|---|---|---|---|---|---|---|
| D-01 (ejemplo de formato; NO defecto constatado) | | | | | | |

## 5. iOS
En macOS abrir proyecto con Xcode, configurar Signing & Capabilities, seleccionar dispositivo iOS, Product > Archive y exportar solo si cuenta y perfil lo permiten. Sin Mac, declarar explícitamente la limitación en el informe. No presentar capturas sintéticas.

## 6. Control de versión y entrega
- `versionCode`: 1 (pendiente de configurar/verificar)
- `versionName`: 1.0.0 (pendiente de configurar/verificar)
- `applicationId`: pendiente de validar en el proyecto real
- Etiqueta requerida: `v1.0-final` **solo después de compilar y verificar el commit exacto**.
- AAB final: `Equipo<N>_ProyectoFinal_Android.aab` (sustituir N por número real)
- APK final: identificador de equipo y versión, consistente con el informe.
- Entrega docente de builds: 16/11/2026; sustentación: 17/11/2026.

## 7. Lista de cotejo
- [ ] Ficha de integración cerrada y congelada.
- [ ] Keystore creado, respaldado y nunca versionado.
- [x] Reglas del .gitignore preparadas.
- [ ] Debug compila sin secretos locales.
- [ ] AAB firmado generado y APK release instalado.
- [ ] Firma verificada y huella registrada.
- [ ] Minificación y flujo funcional verificados.
- [ ] iOS archivado o limitación acompañada de evidencia.
- [ ] Dos teléfonos físicos probados y defectos registrados.
- [ ] Versión / identificador / nombre de archivos coinciden.
- [ ] Commit de build verificado y etiqueta final creada.
