# 🧾 Proyecto 2 — Solnaris ERP 2.0: Plan de Pruebas Manual de Release Candidate

⬅️ [Volver al portafolio](../)

**Estado:** 🟡 En curso — 130 de 308 casos ejecutados (42 %) · 61 incidencias reportadas, 61 cerradas  
**Rol:** QA Tester (testing manual funcional y de regresión)  
**Sistema bajo prueba:** Solnaris ERP 2.0 (evolución de Y2K ERP, desarrollado por Finansoft) — ERP web con facturación electrónica  
**Contexto:** Migración del frontend de AngularJS 1.x a Angular 21 sobre el mismo backend  
**Entorno:** Integración, con backend y validación tributaria reales (no mocks)  
**Fecha:** Septiembre 2026

---

### 📝 Descripción del Proyecto

Solnaris ERP 2.0 reemplaza el frontend legacy de Y2K ERP por uno nuevo en Angular 21. Antes de declararlo **Release Candidate** y retirar el frontend anterior, había que confirmar que las **60 pantallas y flujos reales** del sistema funcionan igual o mejor que en la versión legacy.

Mi trabajo en este proyecto:

- **Ejecución manual** de un plan de pruebas de 308 casos organizado por módulo, siguiendo el mismo orden de navegación del sistema
- **Detección y reporte de incidencias** con severidad, pasos para reproducir y resultado esperado vs. obtenido
- **Re-test de cada corrección** hasta el cierre de la incidencia
- **Pruebas de autorización por rol**, con un usuario administrador y uno con permisos restringidos
- **Validación de documentos tributarios** (facturas, notas de crédito, guías de remisión, retenciones) contra la respuesta real de la autoridad tributaria

---

### 🎯 Objetivos del Proyecto

✅ Confirmar que cada pantalla migrada conserva el comportamiento del sistema legacy  
✅ Detectar regresiones de bugs ya corregidos durante la migración  
✅ Verificar que los documentos electrónicos generados sean aceptados por la autoridad tributaria  
✅ Asegurar que los permisos por rol se apliquen en backend, no solo ocultando opciones del menú  
✅ Dejar evidencia trazable de cada hallazgo, desde el reporte hasta el cierre  

---

### 🔍 Alcance de Testing

#### Cobertura por módulo

| # | Módulo | Qué cubre | Casos | Ejecutados | Estado |
|---|---|---|---|---|---|
| 00 | Transversal | Sesión, permisos, tema claro/oscuro, responsive, exportación, manejo de errores | 19 | 19 | ✅ |
| 01 | Auth y Sesión | Login, olvidé/restablecer contraseña, Mi Perfil, Dashboard | 23 | 23 | ✅ |
| 02 | Ventas / Facturación | Facturar, reporte de facturas, notas de crédito, guías de remisión, reportes de ventas | 32 | 32 | ✅ |
| 03 | Clientes | Mantenimiento, categorías, cobros, cuentas por cobrar, cartera, movimientos | 30 | 30 | ✅ |
| 04 | Proveedores | Mantenimiento, categorías, pagos, cuentas por pagar, cartera, movimientos | 20 | 19 | 🟡 |
| 05 | Compras | Nueva compra, liquidaciones, retenciones, matriz de reglas de retención | 35 | 7 | 🟡 |
| 06 | Inventario | Productos, kardex, stock, recetas, producción, producción por lotes | 32 | 0 | ⏳ |
| 07 | Contabilidad | Plan de cuentas, centros de costo, asientos, libros, balances, flujo de caja | 46 | 0 | ⏳ |
| 08 | ATS | Anexo transaccional: configuración, períodos, generación, historial | 13 | 0 | ⏳ |
| 09 | Administración | Configuración, sucursales, usuarios, roles, tablas, menú | 34 | 0 | ⏳ |
| 10 | Pagos públicos | Compra de plan y solicitud de firma electrónica vía pasarela de pago | 24 | 0 | ⏳ |
| | **Total** | **60 pantallas y flujos** | **308** | **130** | **42 %** |

#### Tipos de Testing Aplicados
```
📋 Testing Funcional por pantalla y por flujo
📋 Testing de Regresión (migración AngularJS → Angular 21)
📋 Testing de Autorización por rol (usuario ROOT vs. rol restringido)
📋 Testing de Integración con la autoridad tributaria (aceptación de comprobantes)
📋 Testing de Reglas de Negocio (matriz de retención emisor × proveedor)
📋 Testing de Consistencia de datos entre pantallas (Cobros vs. CxC vs. Cartera)
📋 Testing de UI: tema claro/oscuro y responsive (laptop 1366×768 y móvil 430×932)
📋 Testing Exploratorio (hallazgos fuera del plan registrados como LIBRE-n)
```

---

### 🛠️ Herramientas y Entorno

```
Documentación de casos:   Markdown con checklists (un archivo por módulo)
Control de versión:       Git (avance de ejecución trackeable por commit)
Análisis funcional:       Excel (HU, flujos, reglas de negocio, CA en Gherkin)
Inspección:               DevTools del navegador (red, consola, simulación de caída de conexión)
Entorno:                  Integración con backend real
Usuarios de prueba:       2 (ROOT + rol restringido creado para el test)
Datos de prueba:          Prefijo QA- para no tocar datos reales del tenant
```

---

### 📊 Resultados del Testing

**Casos diseñados:** 308  
**Casos ejecutados:** 130 (42 %)  
**Incidencias reportadas:** 61  
**Incidencias cerradas y re-testeadas:** 61 (100 %)

| Severidad | Criterio | Cantidad |
|---|---|---|
| 🔴 Bloqueante | Impide completar el flujo o pierde/corrompe datos | 1 |
| 🟠 Alto | El flujo termina, pero con un resultado incorrecto | 27 |
| 🟡 Medio | Validación faltante, mensaje genérico o caso límite mal manejado | 16 |
| ⚪ Bajo | Cosmético, UX o diferencia menor respecto al legacy | 17 |

### 🐛 Hallazgos destacados

Los IDs corresponden al módulo del plan: PERF = Mi Perfil, FACT = Facturación, NC = Nota de Crédito, CXC = Cuentas por Cobrar, CART = Cartera, MOVPROV = Movimientos de Proveedor, TRANS = Transversal.

| ID | Severidad | Hallazgo | Por qué importa |
|---|---|---|---|
| PERF-06 | Bloqueante | Un usuario con rol restringido no podía cambiar su propia contraseña desde Mi Perfil; con el administrador sí funcionaba | Solo se detectó porque probé con dos roles distintos. Con el usuario administrador el bug quedaba oculto |
| FACT-04 | Alto | Al aplicar descuentos por producto, la pantalla mostraba totales correctos pero la autoridad tributaria rechazaba la factura por diferencias en el cálculo | La pantalla "se veía bien": el oráculo real era la respuesta del ente tributario |
| NC-02 | Alto | Una nota de crédito por devolución parcial generaba un subtotal negativo y el comprobante era devuelto por error de esquema | Afecta un flujo legal obligatorio |
| CXC-02 | Alto | El mismo cliente mostraba montos y cantidad de facturas pendientes distintos en Cobros y en Cuentas por Cobrar | Detectado cruzando datos entre pantallas, no probándolas aisladas |
| CART-02 | Alto | La fecha de corte de Cartera excluía las facturas emitidas en el mismo día | Caso límite de fecha/hora: los reportes del día quedaban incompletos |
| MOVPROV-02 | Alto | Las anulaciones de cobros y pagos no aparecían en los movimientos de cliente y proveedor | Rompía la trazabilidad del saldo |
| TRANS-02 | Alto | Después de iniciar sesión, el sistema no devolvía al usuario a la pantalla que había solicitado | Regresión respecto al comportamiento esperado de sesión |

---

### 🧭 Metodología

**1. Diseño de casos desde fuentes reales, no desde una plantilla genérica**
- Las rutas y permisos reales de la aplicación, para no dejar ninguna pantalla sin cubrir
- La bitácora de migración, para marcar bugs ya corregidos como **regresión a confirmar**
- Los patrones compartidos de la UI (carga, exportación, paginación, guardado), para probarlos una sola vez como chequeos **transversales** y referenciarlos por código

**2. Criterio de severidad acordado antes de ejecutar**, para que la clasificación no dependa de la percepción de cada tester.

**3. Plantilla única de incidencia:**

| ID caso | Severidad | Qué pasó | Pasos para reproducir | Resultado esperado vs. real |
|---|---|---|---|---|

**4. Ciclo de vida de cada hallazgo:**
```
Ejecución → Reporte → Corrección (desarrollo) → Re-test → ✅ Cerrado
```

**5. Hallazgos fuera del plan** se registran igual, con ID `LIBRE-n`, para no perder lo encontrado en exploración.

---

### 📂 Cómo está organizado el plan

El plan completo es un documento interno de la empresa y no se publica en este repositorio. Su organización es:

```
plan-de-pruebas-rc/
├── README.md                    # Objetivo, convenciones, entorno e índice
├── 00-transversal.md            # Chequeos que aplican a todas las pantallas
├── 01-auth-sesion.md … 10-pagos-publicos.md   # Un archivo por módulo
└── incidencias.md               # Resumen consolidado de hallazgos
```

Cada archivo de módulo contiene los casos como checklist (`- [ ]` / `- [x]`) y, al final, su tabla de **Incidencias encontradas** con estado, severidad y nota de resolución.

---

### 🧩 Antecedente

Antes de este plan documenté el análisis funcional de los módulos de acceso del sistema legacy (Login y Restablecer Contraseña). Ese trabajo fue la base para entender las reglas de autenticación y sesión que luego verifiqué en la versión 2.0 (módulo 01 — Auth y Sesión).

➡️ Ver [Proyecto 1 — Análisis Funcional de Y2K ERP](../1-Y2K-QA-ANALISIS-FUNCIONAL/)

---

### 💡 Aprendizajes Clave

1. **Probar con un solo rol oculta bugs** — el único bloqueante del proyecto apareció recién con el usuario de permisos restringidos.
2. **La pantalla no es el oráculo** — en facturación, un total que se ve correcto puede ser rechazado por la autoridad tributaria. El resultado esperado real es la aceptación del comprobante.
3. **Cruzar pantallas encuentra lo que la prueba aislada no ve** — Cobros, CxC y Cartera leen los mismos datos y deben coincidir.
4. **Las fechas límite son casos de prueba por sí mismas** — "hoy", fin de día y cambios de formato de fecha generaron varios hallazgos.
5. **Un buen reporte acelera el fix** — pasos reproducibles y esperado vs. real permitieron cerrar las 61 incidencias.

---

### 🚀 Próximos Pasos

- Completar la ejecución de Proveedores y Compras (incluida la matriz de retenciones)
- Ejecutar Inventario, Contabilidad, ATS, Administración y Pagos públicos
- Publicar muestras anonimizadas de casos de prueba y reportes de incidencia
- Consolidar el informe final de Release Candidate con métricas por módulo

---

⬅️ [Volver al portafolio](../) · 📬 [LinkedIn](https://www.linkedin.com/in/niurys-hernandez)
