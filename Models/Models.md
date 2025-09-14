 📘 MODELO

## 🔹 ¿Qué es un modelo?

    - Un modelo es una clase de python, que se usa para definir:
      a-La Tabla de la db
      b- Los campos.
      c-Las relaciones con los otros modelos.
      d- Las reglas de negocio. ( Los metodos, restricciones, herencias de otros modelos).
      e- Comportamiento automatico del modelo.

---

## 🔹 1- TIPOS DE MODELOS.

**model.Model**
    
    Es el modelo más común.
    Crea una tabla real en PostgreSQL.
    Ej: res.partner, sale.order.

**models.TransientModel**

    Es para modelos temporales.
    Crea tablas temporales y es ideal para wizards y configuraciones temporales.

**models.AbstractModel**

    No crea tabla propia.
    Es usado para transmitir herencia de una clase a otra.
    Clase donde definimos reglas de negocio reaprovechables para otras clases.

    
## 🔹 2- CAMPOS
    
    -Los campos basicos se definen como en las clases de Python.
    - Chart, Text, Float, Boolean, Integer, Date ,Datetime ,Binary , Selection.

**Relaciones**

    Las relaciones son como en sql. 
    Many2one N:1
    One2Many 1:N
    Many2many N:N

**Opciones comunes**

    string="..." -> Etiqueta visible.
    required -> Obligación del campo.
    default -> Valor por defecto del atributo de la clae.
    index -> indice en DB.
    Tracking -> se guarda en chatter.
    store = Ture -> guarda en DB.


## 🔹3- METODOS.

**CREATE**

    create(vals)
    -> Crea registros.
    -> Vals: diccionario con valores.
    -> Se puede sobreescribir 

    @api.model
        def create(self, vals):
            if vals.get("price", 0) < 0:
                raise ValidationError("Price cannot be negative")
            return super().create(vals)

**WRITE**

    write(vals)
    -> Actualiza registros.

    def write(self, vals):
        res = super().write(vals)
            if "state" in vals:
                self.message_post(body=f"State changed to {vals['state']}")
            return res

**UNLINK()**

    unlink()
    -> Elimina registros.

    def unlink(self):
        for rec in self:
            if rec.state == "done":
                raise ValidationError("Cannot delete completed records")
            return super().unlink().
        
**MÉTODOS DE BÚSQUEDA**

    -Search.        -filtered
    -browse.        -sorted
    -search-count.  -mapped
    -read


**SUPER()**


## 🔹4- DECORADORES.

    -Un decorador es como ponerle una etiqueta a un metodo para que Odoo sepa cuándo y cómo ejecutarlo.
    -*SIN el decorador, Odoo ve la función normal.
    -*CON el decorador, Odoo sabe que se usa de cierta manera.

**IMPORTANTES**

**@api.model**

    Es usado cuando el metodo trabaja a nivel general del modelo.
    Se usa cuando solo necesitas acceso al entorno (self.env)

    @api.model
        def default_get(self, fields):
            res = super().default_get(fields)
            res["responsible_id"] = self.env.user.id
        return res

**@api.depends**

    Es usado en campos calculados.
    -> Se recalcula este valor si cambiar los campos.

    total = fields.Float(compute="_compute_total")

    @api.depends("price", "tax")
        def _compute_total(self):
            for record in self:
                record.total = record.price * (1 + record.tax)



**@api.contrains()**

    Se usa para validaciones al guardar.
    Se ejecuta al guardar el registro.

    @api.constrains("price")
    def _check_price(self):
        for record in self:
            if record.price < 0:
                raise ValidationError("Price cannot be negative")

    *EJ: Si intentas guardar un precio negativo Odoo lanzará error.

**@api.onchange()**

    Se usa para actualizar valores en el formulario (UI) cuando cambian campos.
    No graba en la base de datos, solo en la vista. 

    @api.onchange("price")
    def _onchange_price(self):
        if self.price > 100:
            self.note = "This is an expensive product!"
    
    Si en la interfaz sale de 100 avisará con la nota que ponemos.





---