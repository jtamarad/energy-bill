# AIA 1 – Chatbot Web Consulta de Stock – Entel Perú

Repositorio de entregables para la automatización **AIA 1: Chatbot Web de Consultas de Stock** del proyecto **PDD_MG-MGR-H022-AIA_Entel_Peru_Gestion_Stock_v1.0**.

Responsable de la implementación: **Jerry Támara Dextre**
Cliente: **Entel Perú**
Proveedor: **Miragroup (MRG)**
Fecha de inicio implementación: **25/06/2026**

---

## 📂 Estructura del repositorio

```
energy-bill/ (rama aia1-chatbot-stock-entel)
│
├── README.md                                   ← Este archivo
│
├── docs/
│   ├── PDD_AIA1_Chatbot_Web_Consulta_Stock_v1.0.md     ← PDD (versión MD para vista en GitHub)
│   ├── PDD_AIA1_Chatbot_Web_Consulta_Stock_v1.0.docx   ← PDD (versión Word entregable)
│   ├── Requerimiento_Funcional_Tecnico_AIA1.md         ← RFT versión MD
│   ├── Requerimiento_Funcional_Tecnico_AIA1.docx       ← RFT versión Word entregable
│   ├── Carta_Gantt_AIA1_Chatbot_Stock.xlsx             ← Carta Gantt en Excel
│   ├── Carta_Gantt_AIA1_Chatbot_Stock.csv              ← Carta Gantt en CSV (vista previa)
│   └── Preguntas_Pendientes_Carlos.md                  ← Preguntas abiertas para Carlos
│
├── dataverse/
│   ├── 01_Tabla_Stock_Lurin.md                         ← Esquema tabla stock_lurin
│   ├── 02_Tabla_SKU_Comprometidos.md                   ← Esquema tabla sku_comprometidos
│   ├── 03_Tabla_Usuarios_Habilitados.md                ← Esquema tabla usuarios_habilitados
│   ├── 04_Tabla_PIN_Autenticacion.md                   ← Esquema tabla pin_autenticacion
│   └── 05_Tabla_Log_Consultas.md                       ← Esquema tabla log_consultas
│
├── copilot-studio/
│   ├── README_Configuracion_Agente.md                  ← Paso a paso de configuración Copilot Studio
│   ├── topics/
│   │   ├── 01_Greeting.yaml
│   │   ├── 02_Autenticacion_Solicitar_Correo.yaml
│   │   ├── 03_Autenticacion_Validar_PIN.yaml
│   │   ├── 04_Consulta_Por_SKU.yaml
│   │   ├── 05_Consulta_Por_Descripcion.yaml
│   │   ├── 06_Consulta_Otra_Gerencia.yaml
│   │   ├── 07_Generar_Plantilla_Pedido.yaml
│   │   └── 08_Fallback_Cierre.yaml
│   └── system-prompt.md                                ← Prompt del agente
│
├── power-automate/
│   ├── README_Flujos.md                                ← Lista de flujos requeridos
│   ├── Flow_01_Enviar_PIN_Correo.md
│   ├── Flow_02_Validar_PIN.md
│   ├── Flow_03_Consultar_Stock.md
│   ├── Flow_04_Generar_Plantilla_Excel.md
│   └── Flow_05_Registrar_Log.md
│
├── src/
│   ├── package.json                                    ← Dependencias node (utilidades)
│   ├── normalizador_stock_lurin.js                     ← Script Excel → CSV Dataverse
│   ├── generador_plantilla_pedido.js                   ← Generador plantilla Excel del pedido
│   ├── generador_pin.js                                ← Generador PIN de 6 dígitos
│   └── tests/
│       ├── test_normalizador.js
│       ├── test_generador_plantilla.js
│       └── test_generador_pin.js
│
└── pruebas/
    ├── Plan_de_Pruebas_AIA1.md                         ← Plan de pruebas funcional
    └── Casos_de_Prueba_AIA1.csv                        ← Casos de prueba detallados
```

---

## 🎯 Alcance funcional (resumen)

El chatbot **AIA1** permite a usuarios contratistas y de Entel Perú:

1. **Autenticarse** mediante correo + PIN de 6 dígitos (vigencia 5 min, máx 3 intentos).
2. **Consultar stock** disponible en Lurín por:
   - Código SKU
   - Descripción / Part Number
   - Proyecto / Gerencia
3. **Visualizar stock de su gerencia** y, como información, de otras gerencias.
4. **Generar y descargar** la **plantilla Excel** del pedido (solo SKUs de su gerencia).
5. **NO** crea tickets JIRA desde el chatbot (fuera de alcance en esta fase).

---

## 🧰 Stack tecnológico

| Componente | Tecnología |
|---|---|
| Agente IA | **Microsoft Copilot Studio** (tenant MRG) |
| Base de datos | **Microsoft Dataverse** |
| Orquestación / Conectores | **Power Automate (flows)** |
| Correo (envío PIN) | **Office 365 Outlook connector** (cuenta del agente) |
| Generación Excel | **Office Scripts / Power Automate – Excel Online** |
| IDE local | **Visual Studio Code** |
| Lenguaje utilitarios | **Node.js 18+** (scripts de normalización y pruebas) |
| Repositorio | **GitHub** |

---

## 🚀 Cronograma macro (ver Carta Gantt)

- **25/06 – 26/06**: Definición Dataverse + entorno Copilot Studio
- **27/06 – 30/06**: Maqueta agente + autenticación PIN
- **01/07 – 03/07**: Consultas de stock + plantilla Excel
- **04/07 – 05/07**: Pruebas internas + ajustes
- **06/07 – 07/07**: Despliegue para fase de pruebas con cliente

---

## ❓ Preguntas pendientes para Carlos

Ver: `docs/Preguntas_Pendientes_Carlos.md`
