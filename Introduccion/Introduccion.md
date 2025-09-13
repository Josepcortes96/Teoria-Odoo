 📘 Introducción a Odoo

## 🔹 ¿Qué es Odoo?
Odoo es un **ERP (Enterprise Resource Planning) y CRM de código abierto**, escrito en **Python** y utilizando **PostgreSQL** como motor de base de datos.  
Está diseñado de forma **modular**, lo que significa que cada funcionalidad (Ventas, Compras, Inventario, Recursos Humanos, Contabilidad, etc.) es un **módulo** que puede instalarse y personalizarse según las necesidades de la empresa.  

👉 Puntos clave:
- Es un **sistema todo en uno**: combina ERP, CRM, e-commerce, gestión de proyectos, facturación, etc.  
- Es **open source** (versión Community), lo que permite extenderlo y personalizarlo.  

---

## 🔹 Arquitectura general de Odoo
La arquitectura de Odoo está organizada en **capas principales**:

1. **Base de Datos (PostgreSQL)**  
   - El motor soportado oficialmente es PostgreeSQL.
   - Odoo es multitenant, es decir, tiene varias bases en un mismo servidor.

2. **Servidor Odoo (Backend en Python)**  
    - El núcleo del sistema del sistema es python: odoo-bin.
    - Esta construido con un ORM(Object-Relational-Mapping), el cual abstrae PostgreeSQL.
    - Los componentes principales son:
        ORM -> Define modelos(models.Model)
        Modular -> Todo son modulos.
        Servicios -> Colas trabajo, API, emails
        Seguridad -> Permisos, ACLS

3. **Frontend**  
   - **Cliente web (backend clásico)**: vistas en XML (listas, formularios, kanban, gráficos…).  
   - **Website / e-commerce**: renderizado con plantillas QWeb (HTML + XML).  
   - **Interfaz en JavaScript (OWL)** para dinamismo y widgets. 
   - **OWL**  Framework de javascript creado por Odoo, basado en componentes y estados de los componentes como React.js

4. **Servicios adicionales**  
   - Motor de reportes (PDF, XLSX, HTML).  
   - API RPC para integraciones.  
   - Módulos de correo, colas de trabajo, etc.  

👉 Esquema simplificado:

        [Navegador / Cliente web]
                │
                ▼
        [Frontend Odoo (JS + QWeb)]
                │
                ▼
        [Servidor Odoo (Python + ORM)]
                │
                ▼
        [Base de datos PostgreSQL]

## 🔹 Community vs Enterprise

### Odoo Community
- **Gratuita y open source**.  
- Incluye los módulos básicos: Ventas, Compras, Inventario, Fabricación, CRM, etc.  
- Ideal para aprendizaje, desarrollo y pequeñas empresas.  
- Limitaciones en contabilidad avanzada, reportes sofisticados y soporte.  

### Odoo Enterprise
- **Versión de pago** (requiere licencia).  
- Incluye TODO lo de Community + características avanzadas:  
  - Contabilidad completa (facturación electrónica, impuestos avanzados).  
  - Recursos Humanos extendido (planificación, evaluación de desempeño).  
  - Helpdesk, firma digital, estudios avanzados de informes.  
  - Aplicaciones móviles oficiales.  
- Soporte y actualizaciones garantizadas por Odoo S.A.  

👉 En resumen:
- **Community** → gratis, flexible, ideal para developers y pequeñas implementaciones.  
- **Enterprise** → de pago, pensada para empresas que necesitan soporte y módulos avanzados.  

---