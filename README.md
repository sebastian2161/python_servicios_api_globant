# 🌐 Python Services API

Este proyecto proporciona el desarrollo completo de **servicios API RESTful** utilizando **Python + Flask**, permitiendo cargar, consultar, respaldar y restaurar datos a una base de datos SQLite. La API está diseñada para simular operaciones reales de backend y puede ser consumida desde **Postman**.

---

## 📋 Características Principales

- ✅ Carga masiva de datos a través de archivo JSON.
- ✅ Respaldo de tablas en formato **Avro**.
- ✅ Restauración de tablas desde archivos **Avro**.
- ✅ Servicios REST para consultas analíticas.
- ✅ Base de datos **SQLite** portátil.
- ✅ Compatible con entorno **Postman Cloud**.

---

## 🚀 Estructura del Proyecto

```
python_servicios_api_globant/
├── api/
│   ├── main.py                # Inicia el servidor Flask
│   ├── formatting_csv_json.py # Convierte CSV a JSON
│   ├── backup_tablas.py       # Realiza backup en formato Avro
│   ├── restore_tabla.py       # Restaura desde Avro
├── data/
│   ├── departments.csv
│   ├── jobs.csv
│   └── hired_employees.csv
├── instance/
│   └── dataweb.db             # Base de datos SQLite
├── backup_tablas/            # Backups en Avro
├── requirements.txt          # Librerías necesarias
└── README.md
```

---

## ⚙️ Requisitos Previos

- Python 3.9
- Sistema operativo Windows 10 (desarrollado y probado).
- Virtual Environment recomendado.
- Cuenta activa en Postman: [https://www.postman.com](https://www.postman.com)

---

## 🧪 Instalación y Ejecución Paso a Paso

### Paso 1: Preparar entorno virtual

```bash
mkdir venv
cd venv
python -m venv myenv
source myenv/Scripts/activate  # En Windows
```

### Paso 2: Instalar dependencias

```bash
pip install -r requirements.txt
```

### Paso 3: Formatear datos a JSON para Postman

```bash
python formatting_csv_json.py
```
- Esto genera `structure_data_postman.json` para cargar en Postman.

### Paso 4: Ejecutar servidor Flask

```bash
python main.py
```
- El servidor estará disponible en `http://127.0.0.1:3000`

### Paso 5: Cargar datos desde Postman (POST)

- Importar `structure_data_postman.json` en Postman.
- Configurar `POST http://127.0.0.1:3000/api/v1/load`
- Seleccionar `Body > raw > JSON` y enviar la carga.

### Paso 6: Respaldar Tablas

```bash
python backup_tablas.py
```
- Se crearán archivos `.avro` en la carpeta `backup_tablas/`

### Paso 7: Restaurar Tablas

```bash
python restore_tabla.py
```
- Se restaurarán los datos a `dataweb.db`

### Paso 8: Consultar Endpoints (GET)

- `GET http://127.0.0.1:3000/api/v1/query1`
    - Contrataciones por trimestre y departamento en 2021.

- `GET http://127.0.0.1:3000/api/v1/query2`
    - Departamentos con contrataciones sobre el promedio en 2021.

---

## 💻 Visualizar Base de Datos SQLite (Web)

1. Instalar extensión: [SQLite Viewer Chrome](https://chromewebstore.google.com/detail/sqlite-viewer/bpedjnknnoaegoaejefbodcdjmjkbbea?hl=es)
2. Subir `dataweb.db` desde carpeta `instance/`
3. Consultas sugeridas:

```sql
SELECT name, sql FROM sqlite_master WHERE type='table';
SELECT * FROM departments;
SELECT * FROM jobs;
SELECT * FROM hired_employees;
```

---

## 📦 Librerías Utilizadas (requirements.txt)

```
blinker==1.7.0
fastavro==1.9.0
flask==3.0.0
flask-sqlalchemy==3.1.1
numpy==1.26.2
pandas==2.1.3
SQLAlchemy==2.0.23
requests==2.31.0
```

---

## 📚 Recursos Adicionales

- [Flask Oficial](https://flask.palletsprojects.com/)
- [FastAvro Docs](https://fastavro.readthedocs.io/en/latest/)
- [SQLite Docs](https://www.sqlite.org/docs.html)
- [Postman Platform](https://www.postman.com/)

---

## 👨‍💼 Autor y Repositorio

- GitHub: [python_servicios_api_globant](https://github.com/sebastian2161/python_servicios_api_globant)
- Rama principal: [main](https://github.com/sebastian2161/python_servicios_api_globant/tree/main)
- Desarrollador: [sebastian2161](https://github.com/sebastian2161)

---

## 🚧 Licencia

Este proyecto es de código abierto. Consulta LICENSE si está disponible.
