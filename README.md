# Portafolio QA — Niurys

> **QA Tester Jr.** | Montevideo, Uruguay
> Formación autodidacta · Buscando primera oportunidad en testing

¡Hola! Soy Niurys, tester en formación. Este portafolio reúne mi trabajo práctico aplicando técnicas de QA sobre un caso de estudio real: el sistema **Y2K — ERP**.

---

## Sobre el caso de estudio: Y2K

Y2K es un sistema ERP que cubre los módulos **Ventas, Clientes, Compras, Inventario y Contabilidad**. Para cada Historia de Usuario (HU) trabajada, este portafolio incluye:

- **Análisis funcional**: historia de usuario, criterios de aceptación, flujos.
- **Reglas de negocio**: cada validación documentada y trazable.
- **Casos de prueba**: planilla Excel con casos positivos, negativos y de borde.
- **Reporte de defectos**: planilla Excel con bugs documentados (severidad, prioridad, evidencia).
- **Escenarios Gherkin**: redacción BDD lista para automatización.

---

## Estructura del portafolio

```
02-PORTFOLIO/
├── Y2K-sistema-ERP/                    Análisis y testing manual por HU
│   ├── HU-01-login/
│   ├── HU-02-reset-password/
│   ├── HU-03-mantenimiento-clientes/
│   └── HU-04-ventas/                   (próxima)
│
├── automation-cypress/                 Pruebas E2E con Cypress
│   ├── login.spec.cy.js
│   └── clientes.spec.cy.js
│
└── api-testing-postman/                Pruebas de API con Postman
    ├── Y2K-coleccion.postman_collection.json
    └── Y2K-environment.postman_environment.json
```

---

## Habilidades demostradas

### Testing manual
- Análisis funcional y descomposición de Historias de Usuario.
- Diseño de casos de prueba aplicando: clases de equivalencia, valores límite, tablas de decisión.
- Reporte de defectos con criterios profesionales (severidad vs prioridad, pasos reproducibles, evidencia).

### Automatización
- **Cypress** — pruebas E2E para flujos críticos.
- **Postman** — colección de pruebas API con scripts de validación.

### Metodologías
- **BDD** con Gherkin (Dado / Cuando / Entonces).
- ISTQB Foundation Level — en formación.

### Herramientas
- Excel para gestión de casos y reporte de defectos.
- Git / GitHub para versionado.
- Postman, Cypress, Chrome DevTools.

---

## Cómo navegar este repo

Si sos reclutador o tech lead, te recomiendo arrancar por:

1. **Cualquier carpeta `HU-XX/`** → leé la historia de usuario y revisá los archivos de casos de prueba (`.xlsx`).
2. **`automation-cypress/`** → mirá los specs para ver cómo aplico los casos en automatización.
3. **`api-testing-postman/`** → revisá los tests con assertions sobre status, payload y persistencia entre requests.

---

## Contacto

- **LinkedIn:** [Pegar URL]
- **Email:** [Pegar email]
- **Ubicación:** Montevideo, Uruguay

---

*Este portafolio se actualiza semanalmente con nuevas HUs y pruebas. Última actualización: ver historial de commits.*
