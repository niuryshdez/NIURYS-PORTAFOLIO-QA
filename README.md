# Portafolio QA — Niurys Hernández

> **QA Funcional** | Montevideo, Uruguay  
> Experiencia práctica en testing funcional sobre sistemas ERP reales en producción

¡Hola! Soy Niurys, QA Funcional con experiencia desde 2023. Este portafolio reúne mi trabajo aplicando técnicas de QA sobre un sistema real en producción: **Y2K — ERP contable SaaS** desarrollado y comercializado por Finansoft.

---

## 🎯 Sobre el caso de estudio: Y2K ERP

Y2K es un sistema ERP contable SaaS multi-tenant para PYMES, desarrollado con CodeIgniter 3 (PHP) + AngularJS 1.x + MySQL/MariaDB. El sistema cubre los módulos de **Ventas, Clientes, Compras, Inventario, Contabilidad y Facturación electrónica (integración SRI Ecuador)**.

Los módulos documentados en este portafolio son:

| Módulo | HU | Estado |
|--------|-----|--------|
| Login / Autenticación | HU-01 | ✅ Disponible |
| Restablecer Contraseña | HU-02 | ✅ Disponible |
| Alta y Edición de Clientes | HU-03 | 🔜 Próximamente |
| Contactos Adicionales | HU-04 | 🔜 Próximamente |

Para cada Historia de Usuario (HU) este portafolio incluye un Excel con **7 hojas integradas**:

- **Historia de Usuario** — propósito, actores, precondiciones, contexto técnico
- **Flujos** — flujo principal + flujos alternativos documentados paso a paso
- **Reglas de Negocio** — cada regla trazable a su fuente (código fuente + manuales)
- **Criterios de Aceptación** — escenarios en formato Gherkin (Given/When/Then)
- **Validaciones** — campos, valores límite (BVA), seguridad y datos de prueba
- **Puntos de Falla** — riesgos anticipados categorizados por criticidad
- **Resumen Ejecutivo** — métricas y hallazgos del análisis

---

## 🏗️ Estructura del portafolio

```
📂 1 — Y2K-QA-Analisis-Funcional (este repo)
│
├── 📂 Analisis-Funcional/
│   ├── Analisis_Funcional_HU_01_LOGIN_Y2K.xlsx              ✅ Disponible
│   ├── Analisis_Funcional_HU_02_CAMBIAR_CONTRASEÑA_Y2K.xlsx ✅ Disponible
│   ├── Analisis_Funcional_HU_03_CLIENTES_Y2K.xlsx           🔜 Próximamente
│   └── Analisis_Funcional_HU_04_CONTACTOS_Y2K.xlsx          🔜 Próximamente
│
├── 📂 Planes-de-Prueba/                                      🔜 Próximamente
│   └── Plan-de-Pruebas-Y2K.docx
│
├── 📂 Casos-de-Prueba/                                       🔜 Próximamente
│   ├── TC-HU-01-Login.xlsx
│   ├── TC-HU-02-ResetPassword.xlsx
│   ├── TC-HU-03-Clientes.xlsx
│   └── TC-HU-04-Contactos.xlsx
│
├── 📂 Reportes-Defectos/                                     🔜 Próximamente
│   └── defectos-encontrados.xlsx
│
└── 📂 SQL-QUERIES/                                           🔜 Próximamente
    └── SQL-QUERIES-QA-Y2K.md


📂 2 — Y2K-QA-Automatizacion-Cypress                🔜 Próximamente
│
└── 📂 cypress/e2e/
    ├── login.cy.js
    └── reset-password.cy.js


📂 3 — Y2K-QA-API-Postman                           🔜 Próximamente
│
├── 📂 Collections/
│   ├── Y2K-Auth.postman_collection.json
│   ├── Y2K-Clientes.postman_collection.json
│   └── Y2K-Facturacion.postman_collection.json
└── 📂 Environments/
    └── Y2K-Dev.postman_environment.json
```

---

## 📊 Métricas del análisis funcional

| HU | Módulo | RN | CA | Flujos | Puntos de Falla |
|----|--------|----|----|--------|-----------------|
| HU-01 | Login | 25 | 21 | 9 | 17 |
| HU-02 | Reset Password | 25 | 19 | 9 | 13 |
| HU-03 | Alta/Edición Clientes | 33 | 21 | 16 | 21 |
| HU-04 | Contactos Adicionales | 28 | 22 | 17 | 18 |
| **Total** | **4 módulos** | **111** | **83** | **51** | **69** |

---

## 🛠️ Habilidades demostradas

### Testing funcional
- Análisis funcional desde código fuente, manuales y entrevistas con el dev
- Extracción de Reglas de Negocio con trazabilidad a la fuente
- Diseño de Criterios de Aceptación en formato Gherkin (BDD)
- Técnicas: Boundary Value Analysis (BVA), partición de equivalencias
- Identificación proactiva de riesgos de seguridad (enumeración de usuarios, multi-tenancy, DELETE+INSERT sin transacción)
- Documentación con trazabilidad completa TC → CA → RN → PF

### Automatización
- **Cypress** — pruebas E2E para flujos críticos (próximamente)
- **Postman** — pruebas de API REST (próximamente)

### Metodologías y herramientas
- BDD con Gherkin
- Git / GitHub
- Excel para análisis funcional y casos de prueba
- Formación: ISTQB Foundation Level (en curso)

---

## 🔍 Hallazgos de seguridad documentados

Durante el análisis funcional se identificaron y documentaron hallazgos reales:

- **Enumeración de usuarios** en Login — mensajes de error diferenciados permiten identificar usuarios válidos del sistema
- **Validación de límites solo en frontend** en Contactos Adicionales — bypasseable vía API directa
- **Riesgo transaccional en DELETE+INSERT** sin transacción de BD en gestión de contactos

---

## 🚀 Cómo navegar este repo

Si sos reclutador o tech lead, te recomiendo:

1. **Abrí cualquier Excel de `analisis-funcional/`** → revisá la hoja "Resumen Ejecutivo" para ver métricas y hallazgos de cada módulo
2. **Hoja "CA — Gherkin"** → criterios de aceptación documentados en BDD
3. **Hoja "Puntos de Falla"** → análisis de riesgos anticipados por criticidad

---

## 📬 Contacto

- **LinkedIn:** [linkedin.com/in/niurys-hernandez](https://www.linkedin.com/in/niurys-hernandez)
- **Email:** niuryshdez@gmail.com
- **Ubicación:** Montevideo, Uruguay

---

*Portafolio en construcción activa — se actualiza con nuevas HUs, casos de prueba y automatización. Ver historial de commits.*
