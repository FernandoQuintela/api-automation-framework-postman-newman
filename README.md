# 🧪 API Testing – JsonPlaceholder
Proyecto demostrativo de automatización de pruebas de API con Postman, Newman y Node.js.


Colección Postman + Newman que valida operaciones CRUD y flujos completos sobre el endpoint `/posts` de la API pública [jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com).

---

## 📂 Estructura

- **Colección:** `jsonplaceholder_tests.postman_collection.json`
- **Environments:** `dev`, `qa`, `prod`, `qa_simulated`
- **Data:**  
  - `data/posts_data.json` (para flujos CRUD data-driven)  
  - `data/negativos_posts.json` (para pruebas negativas)
- **Reports:** `/reports/` (salida HTML de cada run)

---

## 🚀 Cómo ejecutar

### 🔹 Desde NPM

```bash
npm run test:dev       # suite completa en DEV
npm run test:qa        # suite completa en QA
npm run test:qa-sim    # negativos simulados
npm run test:prod      # suite completa en PROD
npm run test:flow      # flujo CRUD data-driven
npm run test:all       # ejecuta todos los anteriores

```

Los reportes se generan automáticamente en la carpeta /reports/
con nombres del tipo report_<entorno>_YYYYMMDD_HHmmss.html.

---

## 📊 Reporte HTML (htmlextra)

### El reporte incluye:


Resumen de iteraciones, requests y assertions

Detalle por request: headers, body y logs de consola

Colores y métricas de performance

Resultados separados por entorno y tipo de test

---

| Tipo de test    | Propósito                                                    | Dataset / Folder | Entorno      |
| --------------- | ------------------------------------------------------------ | ---------------- | ------------ |
| **Contrato**    | Validar status, schema y tipos por endpoint                  | `/posts`         | Dev, QA      |
| **Flujo (DDT)** | Validar secuencia Create → Update → Delete con 3 iteraciones | `Flow DDT`       | QA           |
| **Negativos**   | Validar manejo de errores y reglas de negocio                | `Negativos`      | QA Simulated |
| **Auth Smoke**  | Confirmar envío correcto del header Authorization            | `Auth Smoke`     | Todos        |

---

## 🧰 Reintentos (Retry System)

Cada request crítica cuenta con un sistema de reintentos automático (maxRetries = 3) que maneja errores temporales de red o status 5xx, evitando falsos negativos.

---

## 📦 Dependencias


Node.js 20+

Newman y newman-reporter-htmlextra

### Instalar con:

npm install -g newman newman-reporter-htmlextra

---

## ⚙️ Script y Descripción


| Script       | Descripción                                         |
|--------------|-----------------------------------------------------|
| `test:dev`   | Ejecuta colección completa en entorno **Dev**       |
| `test:qa`    | Ejecuta colección completa en **QA**                |
| `test:qa-sim`| Ejecuta negativos simulados (**QA Simulated**)      |
| `test:prod`  | Ejecuta colección completa en **Prod**              |
| `test:flow`  | Ejecuta solo el folder **“Flow DDT”**               |
| `test:all`   | Ejecuta todos los anteriores en cadena              |

---

## 📁 Reports

Cada run genera un HTML independiente dentro de /reports/.

### Los nombres siguen el formato:

report_<entorno>_YYYYMMDD_HHmmss.html

---

## 🧩 Integración Continua (CI/CD)

Este proyecto ejecuta pruebas automatizadas de API mediante **GitHub Actions**, con generación y despliegue automático de reportes en **GitHub Pages**.

Cada ejecución (push o manual) dispara un workflow que:
1. Instala dependencias (`Node.js`, `Newman`, `htmlextra`).
2. Corre las suites configuradas (Contrato + Smoke).
3. Genera un reporte HTML.
4. Publica automáticamente el resultado en línea.

🔘 **Ejecución manual:**  
Desde la pestaña **Actions**, seleccionar el workflow `api-tests.yml` y presionar **“Re-run all jobs”** para regenerar el reporte.

📄 **Último reporte publicado:**  
👉 [Ver reporte QA en vivo](https://fernandoquintela.github.io/api-automation-framework-postman-newman/)

---

## 🧠 Autor

Fernando Quintela
QA Automation Engineer / Postman–Newman Enthusiast

📍 Buenos Aires, Argentina

📧 fernand.quintela@gmail.com

---

📁 Repositorio de práctica – Pruebas automatizadas sobre API REST.
