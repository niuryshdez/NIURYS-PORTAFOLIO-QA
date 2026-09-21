# 🧩 Proyecto 1 — Análisis Funcional de Y2K ERP (legacy)

⬅️ [Volver al portafolio](../)

**Sistema:** Y2K ERP, ERP contable SaaS multi-tenant para PYMES, desarrollado por Finansoft  
**Tecnología:** CodeIgniter 3 (PHP) · AngularJS 1.x · MySQL/MariaDB  
**Módulos del sistema:** Ventas, Clientes, Compras, Inventario, Contabilidad y Facturación electrónica (SRI Ecuador)  
**Mi rol:** Análisis funcional de los módulos de acceso (Login y Restablecer Contraseña) para derivar criterios de aceptación y riesgos de prueba

---

## 📑 Historias de usuario analizadas

| HU | Módulo | Documento | Estado |
|---|---|---|---|
| HU-01 | Login / Autenticación | [ANALISIS_FUNCIONAL_HU_01_LOGIN_Y2K.xlsx](DOCUMENTOS/ANALISIS_FUNCIONAL_HU_01_LOGIN_Y2K.xlsx) | ✅ Publicada |
| HU-02 | Restablecer Contraseña | [ANALISIS_FUNCIONAL_HU_02_CAMBIAR CONTRASEÑA_Y2K.xlsx](DOCUMENTOS/ANALISIS_FUNCIONAL_HU_02_CAMBIAR%20CONTRASE%C3%91A_Y2K.xlsx) | ✅ Publicada |

Cada Excel contiene **7 hojas integradas**:

- **Historia de Usuario**: propósito, actores, precondiciones y contexto técnico
- **Flujos**: flujo principal y flujos alternativos, paso a paso
- **Reglas de Negocio**: cada regla trazable a su fuente (código fuente y manuales)
- **Criterios de Aceptación**: escenarios en Gherkin (Given / When / Then)
- **Validaciones**: campos, valores límite (BVA), seguridad y datos de prueba
- **Puntos de Falla**: riesgos anticipados, clasificados por criticidad
- **Resumen Ejecutivo**: métricas y hallazgos del análisis

---

## 📊 Métricas del análisis

| HU | Módulo | Reglas de negocio | Criterios de aceptación | Flujos | Puntos de falla |
|---|---|---|---|---|---|
| HU-01 | Login | 25 | 21 | 9 | 17 |
| HU-02 | Restablecer Contraseña | 25 | 19 | 9 | 13 |
| **Total** | **2 módulos** | **50** | **40** | **18** | **30** |

---

## 🔍 Hallazgos de seguridad documentados

Durante el análisis identifiqué este riesgo antes de ejecutar pruebas:

- **Enumeración de usuarios en Login (HU-01):** los mensajes de error diferenciados permiten saber si un usuario existe en el sistema.

---

## 🧭 Cómo leer los documentos

1. Abre cualquier Excel de la carpeta [`DOCUMENTOS/`](DOCUMENTOS/). GitHub no muestra el contenido del Excel en pantalla: usa el botón **Download** (descargar).
2. Empieza por la hoja **Resumen Ejecutivo**: métricas y hallazgos del módulo.
3. Sigue con **Criterios de Aceptación**: los escenarios en Gherkin.
4. Termina en **Puntos de Falla**: el análisis de riesgos por criticidad.

---

➡️ **Continuación:** estas reglas y riesgos los verifiqué después en la versión 2.0 del sistema. Ver [Proyecto 2 — Plan de Pruebas RC de Solnaris ERP](../2-SOLNARIS-ERP-QA-TESTING/).
