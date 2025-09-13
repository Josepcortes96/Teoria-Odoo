# 📘 Ejercicios Teóricos sobre Módulos en Odoo

## 🔹 1. Conceptos generales
1. Explica con tus palabras qué es un módulo en Odoo y qué lo diferencia de otros frameworks.  
2. ¿Por qué se dice que un módulo debe ser *autocontenido, fácil de mantener y reutilizable*?  
3. ¿Qué partes (backend, frontend, controladores) pueden vivir dentro de un módulo y cómo se organizan?  

---

## 🔹 2. Estructura del módulo
4. Dibuja la estructura típica de carpetas de un módulo en Odoo y describe para qué sirve cada carpeta.  
5. ¿Qué diferencia hay entre la carpeta `data/` y la carpeta `demo/`? ¿Cuándo usarías cada una?  
6. ¿Para qué sirve la carpeta `wizards/` y en qué se diferencia de un modelo normal en `models/`?  

---

## 🔹 3. Archivos principales
7. ¿Qué es el archivo `__manifest__.py`? Explica por qué **parece JSON pero no lo es**.  
8. Enumera al menos 5 claves del `__manifest__.py` y explica qué significa cada una (`depends`, `data`, `application`, etc.).  
9. ¿Qué pasa si pones en el `manifest` un archivo XML en `data` que no existe?  

10. ¿Qué es `__init__.py` y por qué es obligatorio en cada carpeta (`models/`, `controllers/`, etc.)?  
11. ¿Qué pasa si olvidas poner `__init__.py` en la carpeta `models/` de tu módulo?  

---

## 🔹 4. Modelos y vistas
12. ¿Qué significa que un modelo en Odoo **hereda de `models.Model`**?  
13. ¿Qué diferencia hay entre heredar un modelo con `_inherit = "sale.order"` y crear uno nuevo con `_name = "library.book"`?  
14. ¿Por qué se recomienda que los campos, modelos y archivos tengan nombres en inglés?  

---

## 🔹 5. Seguridad, reportes y tests
15. Explica la diferencia entre **`ir.model.access.csv`** y **record rules (`security.xml`)**.  
    - ¿Cuál controla CRUD global sobre el modelo?  
    - ¿Cuál controla acceso a registros específicos?  
