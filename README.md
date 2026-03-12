# Colección de Pruebas de API (Postman) - Trabajo Final de Ingeniería

Este repositorio contiene la colección oficial de pruebas estructuradas en Postman, desarrollada como anexo técnico para la validación de la arquitectura de microservicios clínicos (`TF_Back` y `fhir_server`).

El objetivo de esta colección es proporcionar al tribunal evaluador un entorno reproducible para auditar tanto la interoperabilidad estructural del sistema (bajo el estándar FHIR R5) como las validaciones de seguridad perimetral y control de accesos.

## 📂 Contenido del Repositorio

* `TF_FHIR_Endpoints.postman_collection.json`: Archivo principal exportado (formato v2.1.0) que contiene todas las peticiones HTTP, cabeceras preconfiguradas y cuerpos (*payloads*) de prueba.

## ⚙️ Requisitos Previos

Para ejecutar estas pruebas, es necesario contar con:
1. [Postman](https://www.postman.com/downloads/) instalado en su equipo (versión de escritorio o web).
2. Credenciales de acceso válidas o un *Token JWT* generado desde el frontend de la aplicación.

## 🚀 Instrucciones de Uso (Importación)

1. Descargue el archivo `.json` de este repositorio.
2. Abra Postman y diríjase a **File > Import** (o presione `Ctrl+O` / `Cmd+O`).
3. Seleccione el archivo descargado para cargar la colección en su *Workspace*.
4. La colección utiliza **Variables de Colección** para facilitar la configuración del entorno. Antes de ejecutar las peticiones, diríjase a la pestaña "Variables" de la colección importada y asegúrese de configurar los siguientes valores según el entorno a evaluar:

| Variable | Descripción | Ejemplo de Valor |
| :--- | :--- | :--- |
| `base_url_tfback` | URL base del backend principal | `https://tubackend-railway.app` |
| `base_url_fhir` | URL base del servidor clínico FHIR | `https://fhirserver-production-fhir.up.railway.app` |
| `access_token` | Token JWT de sesión activa (Nota: no incluir la palabra "Bearer", solo el token) | `eyJhbGciOiJIUzI1NiIsInR...` |

## 🏗️ Estructura de la Colección

Las peticiones están organizadas de manera modular en carpetas lógicas para facilitar la navegación:

* **1. Patient (Pacientes):** Operaciones CRUD sobre recursos de pacientes con formato FHIR R5.
* **2. Practitioner (Usuarios):** Gestión de médicos y personal administrativo.
* **3. DiagnosticReport (Informes):** Creación y consulta de informes de evaluación y anexos.
* **4. DiagnosticReport (Historia Fisiátrica):** Manejo de bundles y extensiones fisiológicas.
* **5. DocumentReference (Archivos):** Gestión de metadatos y almacenamiento de documentos PDF.
* **6. Catálogos (Organization & Location):** Listados parametrizados de mutuales, prestaciones, provincias y ciudades.
* **7. Validaciones de Seguridad (STRIDE):** *(Si se incluyen)* Casos de prueba específicos para auditar la prevención de manipulación de tokens (Tampering), el control de accesos basado en roles (RBAC) y los límites de tasa (Rate Limiting).

## 👨‍💻 Autor
**Ignacio Lopez** *Desarrollado como parte integral de la validación empírica del Trabajo Final de Ingeniería.*