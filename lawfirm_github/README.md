# ⚖️ Justicia & Asociados — LawFirm Management System v2

Sistema de gestión de escritorio para el bufete de abogados **"Justicia & Asociados"**, desarrollado en Python con Tkinter, SQLite, exportación Excel/PDF, validaciones completas, manejo de imágenes y temas visuales.

---

## 📋 Descripción

Aplicación que centraliza la administración del bufete con 4 módulos: **Clientes, Abogados, Casos Legales y Audiencias & Citas**. Implementa CRUD completo con stored procedures en SQLite, exportación a Excel y PDF con filtros, validación estricta de campos y dos temas visuales intercambiables.

---

## 🗂️ Módulos del sistema

| # | Módulo | Funcionalidades |
|---|--------|-----------------|
| 1 | **Clientes** | CRUD, foto (Pillow), exportación Excel/PDF, filtros por tipo/fecha/clasificación |
| 2 | **Abogados** | CRUD, foto (Pillow), exportación Excel/PDF, filtros por especialidad/disponibilidad |
| 3 | **Casos Legales** | CRUD, relación cliente-abogado, exportación Excel/PDF, filtros por estado/rama/fecha |
| 4 | **Audiencias y Citas** | CRUD, relación con caso, exportación Excel/PDF, filtros por tipo/fecha |

---

## 📁 Estructura del proyecto

```
lawfirm_v2/
│
├── main.py           # Aplicación principal — 4 módulos Tkinter
├── db_manager.py     # Módulo DB — conexión SQLite y stored procedures
├── utils.py          # Módulo utilitarios — validaciones, Excel, PDF, Pillow
├── themes.py         # Módulo temas — Claro / Oscuro
│
├── db/
│   ├── lawfirm.sql   # Script SQL — tablas, views, triggers, datos ejemplo
│   └── lawfirm.db    # Base de datos SQLite (se genera automáticamente)
│
├── exports/          # Carpeta de archivos exportados
├── assets/           # Recursos (iconos, imágenes)
│
└── README.md
```

---

## ⚙️ Requisitos

- Python **3.8** o superior
- Las siguientes librerías (ver instalación abajo):

| Librería | Uso |
|----------|-----|
| `tkinter` | GUI (incluida con Python) |
| `tkcalendar` | Selector de fechas con calendario flotante |
| `openpyxl` | Exportación a Excel |
| `reportlab` | Exportación a PDF |
| `Pillow` | Manejo profesional de imágenes |

---

## 🚀 Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/lawfirm.git
cd lawfirm/lawfirm_v2
```

### 2. Instalar dependencias

```bash
pip install tkcalendar openpyxl reportlab Pillow
```

### 3. Ejecutar la aplicación

```bash
python main.py
```

> La base de datos `lawfirm.db` se crea automáticamente en la primera ejecución con datos de ejemplo incluidos.

---

## 🖥️ Uso de la aplicación

### Navegación
- Usa las **4 pestañas** en la parte superior para cambiar de módulo.
- Haz clic en un registro del **listado inferior** para cargarlo en el formulario.

### Botones de acción

| Botón | Función |
|-------|---------|
| 💾 **Guardar** | Valida y guarda el nuevo registro en la base de datos |
| ✏ **Actualizar** | Modifica el registro cargado (pide confirmación) |
| 🗑 **Eliminar** | Elimina el registro seleccionado (pide confirmación) |
| 🧹 **Limpiar** | Vacía todos los campos del formulario |
| 📊 **Excel** | Exporta los datos con los filtros activos a Excel |
| 📄 **PDF** | Exporta los datos con los filtros activos a PDF |

### Menú superior
- **🎨 Tema** → cambia entre **Tema Claro** y **Tema Oscuro**
- **📤 Exportar** → acceso directo a exportación de cualquier módulo

### Filtros de exportación
Cada módulo tiene filtros propios. Aplícalos antes de exportar para obtener reportes específicos:
- **Clientes**: por tipo, rango de fechas, clasificación
- **Abogados**: por especialidad y disponibilidad
- **Casos**: por estado, rama del derecho, rango de fechas
- **Audiencias**: por tipo y rango de fechas

### Gestión de imágenes
En los módulos de Clientes y Abogados:
1. Clic en **📷 Seleccionar foto**
2. Elige un archivo JPG, PNG o GIF (máximo 5 MB)
3. La imagen se redimensiona automáticamente y se guarda en la base de datos

### Validaciones automáticas
- **Campos numéricos** (tarifa, años de experiencia): solo aceptan números
- **Correo electrónico**: valida formato con expresiones regulares
- **Teléfono**: solo dígitos, guiones y paréntesis
- **Campos obligatorios** (marcados con *): requieren mínimo de caracteres
- Los botones Eliminar y Actualizar piden confirmación antes de ejecutarse

---

## 🗄️ Base de datos

La base de datos es **SQLite** con las siguientes tablas:

| Tabla | Descripción |
|-------|-------------|
| `clientes` | Datos de clientes |
| `abogados` | Datos de abogados |
| `casos` | Casos legales |
| `audiencias` | Audiencias y citas |
| `log_eliminados` | Registro automático de eliminaciones (trigger) |

**Stored procedures** implementados como funciones Python en `db_manager.py`:
`sp_insert_*`, `sp_update_*`, `sp_delete_*`, `sp_get_all_*`, `sp_get_*_by_codigo`

**Views** disponibles: `v_clientes`, `v_abogados`, `v_casos`, `v_audiencias`

**Triggers**: `trg_delete_caso`, `trg_delete_cliente` (log automático)

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Versión | Uso |
|------------|---------|-----|
| Python 3 | 3.8+ | Lenguaje principal |
| Tkinter + ttk | Incluido | GUI, pestañas, Combobox, Treeview |
| tkcalendar | 1.6+ | Selector de fechas con calendario flotante |
| SQLite3 | Incluido | Base de datos relacional local |
| openpyxl | 3.x | Exportación a Excel con estilos |
| reportlab | 4.x | Exportación a PDF profesional |
| Pillow (PIL) | 10.x | Carga, redimensionado y almacenamiento de imágenes |

---

## 👨‍💻 Autor

Proyecto universitario — Programación con Python  
Bufete de abogados: **Justicia & Asociados**
