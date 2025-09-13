 📘 MODULOS

## 🔹 ¿Qué es un modulo?

    - Un modulo es la unidad mínima de extensión del sistema. En Odoo todo esta basado en modulos.
    - Todo(desde un nuevo modelo, un reporte, hasta una app entera) és un modulo.
    - En Odoo, todo esta dentro de cada modulo, es decir, la parte del servidor frontend y controladores se   encuentran cada uno dentro de su modulo

👉 Punto crucial:
-  **Un modulo bien diseñado debe ser autocontenido, fácil de mantener y reutilizable.**


---

## 🔹 ESTRUCTURA DE UN MODULO

                mi_modulo/
                    │
                    ├── __manifest__.py       # Metadatos del módulo
                    ├── __init__.py           # Inicialización de imports
                    │
                    ├── models/               # Definición de modelos (clases ORM)
                    │   ├── __init__.py
                    │   └── modelo.py
                    │
                    ├── views/                # Vistas XML (formularios, listas, kanban, etc.)
                    │   └── modelo_views.xml
                    │
                    ├── security/             # Reglas de seguridad
                    │   ├── ir.model.access.csv
                    │   └── security.xml
                    │
                    ├── data/                 # Datos iniciales (parametrización, secuencias, etc.)
                    │
                    ├── demo/                 # Datos demo (solo para modo demo/test)
                    │
                    ├── report/               # Reportes (Qweb PDF, XLSX, etc.)
                    │
                    ├── wizards/              # Asistentes (transacciones interactivas)
                    │
                    ├── static/               # Archivos estáticos (JS, CSS, imágenes)
                    │   └── src/
                    │
                    ├── controllers/          # Controladores web
                    │
                    └── tests/                # Pruebas unitarias/funcionales


1. **ARCHIVOS PRINCIPALES**  
    
    **1.1  __manifest__.py**

    -Es un archivo python, que actua como si fuera el DNI, por así decirlo.
    -Es donde Odoo lee para poder instalar y cargar el modulo que describe.

    **IMPORTANTE** -> AUNQUE PAREZCA UN JSON NO LO ES. YA QUE ODOO ESPERA UN ARCHIVO PYTHON.

    **EJEMPLO DE UN __manifest__ sobre un modulo de Ventas 

        {
                'name': 'Sale Order Custom Fields',
                'version': '16.0.1.0.0',
                'summary': 'Extensión de pedidos de venta con campos y vistas personalizadas',
                'description': """
            Sale Order Custom Fields
            ========================
            Este módulo agrega un campo personalizado en el pedido de venta
            y un menú adicional para análisis de ventas.
                """,
                'author': 'Mi Empresa',
                'website': 'https://miempresa.com',
                'category': 'Sales',
                'license': 'LGPL-3',
                'depends': [
                    'sale',          # depende de Ventas
                    'contacts',      # depende de Contactos
                ],
                'data': [
                    # Seguridad primero
                    'security/ir.model.access.csv',
                    
                    # Vistas (orden recomendado: menús, acciones, vistas)
                    'views/sale_order_views.xml',
                    'views/sale_menu.xml',
                    
                    # Datos de inicialización (ejemplo: secuencias o parámetros)
                    'data/sale_sequence.xml',
                ],
                'demo': [
                    'demo/sale_order_demo.xml',
                ],
                'installable': True,
                'application': False,   # False = módulo técnico, True = app visible
                'auto_install': False,  # se instala solo si las dependencias ya están
        }

    **1.2 __init__.py**

    -Es como en el uso normal de python, no hay ninguna diferencia, es usado para marcar una carpeta como un paquete importable.
    -Con el fin de inicializar el modulo. 

2. **Models**  
    - Se definen en la carpeta models/
    - Vienen heredados de models.Model.
    - Es el corazón de la logica de negocio de Odoo.

3. **Views**  
    - Se definen en la carpeta views/
    - Deben de estar bien estructuradas y comentadas.
    - Mantener consistencia con el modelo.

4. **Datos y demo**  
   -  En la carpeta data/ parametrización (secuencias, vistas, cronjobs).
   -  En la carpeta demo/ datos ficticios (modo demo).

5. **Wizards**
    - Esta diseñada para asistentes interactivas ( ej: generar facturas).
    - Se ubica en la carpeta wizards/

6. **Controladores**
    - Es donde se ubican todos los endpoints. 
    - Ubicados en la carpeta controllers/

7. **Reportes**
    - Esta en la carpeta report/.
    - Definiciones Qweb o XLSX.
    * Evitar la logica pensada en Qweb

8. **Tests**
    - Ubicados en tests/
    - odoo.test.common.TransactionCase // HttpCase

9. **Static**
    - Es donde van ubicados archivos estaticos, como imagenes, tipografias, CSS
    - Carpeta static/






---