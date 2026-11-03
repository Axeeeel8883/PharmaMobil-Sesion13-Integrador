# PharmaMobil — Práctica Integradora N.º 13

Proyecto académico de Desarrollo de Aplicaciones Móviles (Kotlin Multiplatform).

## Ramas
- `main`: inicialización del repositorio.
- `develop`: base de trabajo inicial.
- `feature/integrador-13`: **96 archivos del proyecto docente** (incluido este README adaptado), más 10 archivos de apoyo para sesión 13.

## Código base importado
Se incorporó el proyecto de https://github.com/dreyna/pharmaMobil (rama `master`) a esta rama. Se conservaron sus archivos Gradle, Android, iOS, `shared`, tests y recursos binarios. El README se reemplazó por esta explicación; el resto coincide en ruta y contenido con la referencia al momento de la importación.

## Trabajo de sesión 13
- `integrador13/src/commonMain/kotlin/`: sincronizador desacoplado, modelos de estado e interfaces de permisos y telemetría.
- `integrador13/sql/`: borrador de migración y consultas SQLDelight.
- `shared/src/commonMain/kotlin/pe/edu/upeu/pharmamobil/evidencias/`: clases para registrar evidencias.
- `docs/SESION13-CHECKLIST.md`: lista de pruebas y criterios.
- `docs/SESION13-PLANTILLA-RESULTADOS.md`: plantilla de evidencias.

**Estado de integración:** los archivos bajo `integrador13/` son un kit de desarrollo, todavía no están enlazados con los módulos compilados `androidApp` y `shared`. El proyecto docente importado contiene repositorios en memoria, y no sustituye por sí solo las implementaciones REST, JWT, SQLDelight ni Firebase solicitadas en la guía. No hay compilación, pruebas Android/iOS o capturas reales verificadas en esta entrega.

## Cómo continuar
1. Abrir el proyecto en Android Studio con JDK compatible y sincronizar Gradle.
2. Ejecutar `./gradlew :androidApp:assembleDebug` (Windows: `gradlew.bat :androidApp:assembleDebug`) y anotar resultado real.
3. Integrar los componentes de `integrador13/` en el módulo `shared`, las implementaciones Android en `androidApp`, y el proveedor Firebase en la capa de datos.
4. Implementar y verificar la persistencia, autenticación y sincronización con PharmaSoft.
5. Ejecutar pruebas y recopilar capturas reales de permisos y sincronización.

Fuente docente: https://github.com/dreyna/pharmaMobil
