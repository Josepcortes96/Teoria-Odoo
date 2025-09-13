# 📚 Teoría Odoo  

Repositorio creado por **Josep Cortés Mañanich**, con el objetivo de recopilar **preguntas, teoría y conceptos básicos de Odoo** para facilitar el aprendizaje y servir como material de estudio.  

---

## 🎯 Objetivo  

Este repositorio está pensado para:  
- Aprender la **arquitectura y funcionamiento** de Odoo.  
- Entender la **estructura de un módulo** y el rol del backend (Python + PostgreSQL).  
- Practicar con **preguntas teóricas** organizadas por bloques.  
- Tener un **material de referencia rápido y en español**.  

---

## 🗂️ Contenido  

El contenido está dividido en bloques relacionados con la parte del **servidor (backend en Python)** y la **teoría general de Odoo**:  

1. **Introducción a Odoo**  
   - ¿Qué es Odoo?  
   - Arquitectura general.  
   - Community vs Enterprise.  

2. **Estructura de un módulo**  
   - Archivos principales (`__manifest__.py`, `__init__.py`).  
   - Organización de carpetas (`models`, `views`, `security`, `data`).  

3. **Modelos y ORM**  
   - Diferencias entre `models.Model` y `models.TransientModel`.  
   - Tipos de campos y relaciones.  
   - Métodos básicos del ORM (`create`, `write`, `search`, `unlink`).  

4. **Vistas y Presentación**  
   - Tipos de vistas: lista, formulario, kanban, calendario, gráfico.  
   - Menús y acciones.  
   - Plantillas QWeb.  

5. **Seguridad**  
   - Archivos `ir.model.access.csv`.  
   - Record Rules.  
   - Grupos y permisos de usuario.  

6. **Configuración y despliegue**  
   - Archivo `odoo.conf`.  
   - Parámetro `addons_path`.  
   - Instalación de módulos.  

7. **Banco de preguntas**  
   - Preguntas básicas.  
   - Preguntas sobre ORM.  
   - Preguntas de seguridad.  
   - Preguntas de infraestructura.  

---

## 🤝 Contribución  

Si quieres aportar nuevas preguntas o teoría:  
1. Haz un **fork** del repositorio.  
2. Crea una rama (`git checkout -b mejora-teoria`).  
3. Realiza tus cambios y haz un **commit**.  
4. Envía un **pull request**.  

---

## 📌 Nota  

Este repositorio está en constante crecimiento.  
El objetivo no es sustituir la documentación oficial, sino servir como **apoyo para estudiantes y desarrolladores junior** que quieran empezar en el ecosistema Odoo.  

📖 Documentación oficial: [https://www.odoo.com/documentation](https://www.odoo.com/documentation)  
