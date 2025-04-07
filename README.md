
# 🧪 Everlab ORU File Analyzer — Full Stack Test Project

This project allows doctors to upload HL7 ORU pathology reports and identify **high-risk results** based on diagnostic metrics.

---

## 🛠 Tech Stack

- **Frontend**: React + TypeScript + Tailwind CSS
- **Backend**: Node.js + Express.js
- **Database**: PostgreSQL (via Docker)
- **Containerization**: Docker + Docker Compose

---

## 📦 Project Structure

```
completed_test_project/
├── backend/                # Express API for HL7 parsing + CSV data logic
│   └── data/               # diagnostic_metrics.csv and sample ORU file
├── frontend/               # React + Tailwind UI
├── docker-compose.yml      # Multi-service orchestration
```

---

## 🚀 Getting Started

### 1. **Clone the Repo**
If using the zip:
```bash
unzip completed_test_project.zip
cd completed_test_project
```

---

### 2. **Start Everything with Docker**

```bash
docker-compose up --build
```

- Backend runs on: `http://localhost:5000`
- Frontend runs on: `http://localhost:5173`
- PostgreSQL exposed on port `5432` (user: `everlab`, password: `password`)

---

### 3. **Use the App**

1. Go to [http://localhost:5173](http://localhost:5173)
2. Upload the sample `.oru.txt` file in `/backend/data/MP826520.oru.txt`
3. View the parsed lab results — abnormal ones are flagged as **High Risk**

---

## 🧠 Logic Summary

- ORU file is parsed on the backend using `simple-hl7`
- Each OBX segment is matched to a `diagnostic_metric` using:
  - `oru_sonic_codes`
  - `oru_sonic_units`
- Result values are compared with `everlab_lower` and `everlab_higher`
- Out-of-range values are flagged in the frontend

---

## 🐳 Docker Notes

You can inspect the running containers:
```bash
docker ps
```

To stop services:
```bash
docker-compose down
```

---

## 📌 Environment Variables

Default values (already configured in `docker-compose.yml`):

```
POSTGRES_USER=everlab
POSTGRES_PASSWORD=password
POSTGRES_DB=diagnostics
```

---

## 📬 Contact

Made with ❤️ for the Everlab take-home test.
