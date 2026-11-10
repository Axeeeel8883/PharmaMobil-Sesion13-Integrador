# Sesión 14 — ficha de integración y alcance congelado

Fecha: 10/11/2026. Proyecto: PharmaMobil / PharmaSoft.
Rama de trabajo: `feature/builds-14`.

## Diagnóstico basado en la sesión 13
La documentación existente de la sesión 13 declara que la integración está incompleta. En la rama `develop` no se localizaron `settings.gradle.kts`, `build.gradle.kts` ni un módulo Android compilable en las rutas habituales. No se ha verificado una compilación ni pruebas reales. **No se declaran cerrados los requisitos funcionales.**

| ID | Hueco | Clasificación | Motivo / acción |
|---|---|---|---|
| H-01 | Proyecto KMP completo y configuración Gradle ausentes | Se cierra hoy (pendiente) | Incorporar código fuente completo del proyecto base, respetando dependencias y módulos. |
| H-02 | Login, token y roles con PharmaSoft no verificados | Limitación actual | Requiere backend accesible, integración y prueba de credenciales/roles. |
| H-03 | CRUD y sincronización offline-first no verificados | Limitación actual | Requiere base local, API conectada y pruebas de reconexión. |
| H-04 | Permisos nativos en tres estados sin evidencia | Limitación actual | Requiere implementación y dispositivo físico. |
| H-05 | Compilación/firma iOS sin evidencia | Limitación actual | Requiere macOS, Xcode y firma Apple. |
| H-06 | Builds Android firmados no generados | Se cierra hoy (pendiente) | Depende de H-01, firma y compilación release. |

**Alcance congelado:** no introducir nuevas funcionalidades; concentrarse en cerrar la integración exigida y validar la entrega. Si algo no llega a verificarse, se registra como limitación, nunca como aprobado.

## Registro de cierre
Completar cada fila con evidencia, fecha y resultado después de cada prueba. La clasificación anterior refleja el estado inicial, no un resultado final.
