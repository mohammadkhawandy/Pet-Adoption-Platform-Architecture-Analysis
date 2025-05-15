# Task 4 – Pet Adoption Platform Architecture Analysis

## Full Name:
**Mohammad ibrahim alkhawandy**

---------------------

## Project Description:

A web platform that allows users to view adoptable pets, locate nearby emergency veterinary clinics, and read articles about pet care.  
This analysis was created without actual code (No Code), focusing on system architecture and required APIs.

------------------

## 1. Proposed Project Architecture

### Technologies & Libraries:
- **Node.js + Express.js** – For building a lightweight API
- **MongoDB + Mongoose** – Flexible and scalable NoSQL database


### Folder Structure:
```
Project structure:
├──src/
├  ├── controllers/
├  ├   ├──pets.controllers.js
├  ├   ├──users.controllers.js
├  ├   ├──clinics.controllers.js
├  ├   ├──articles.controllers.js
├  ├── routes/
├  ├    ├──pets.routes.js
├  ├    ├──users.routes.js
├  ├    ├──clinics.routes.js
├  ├    ├──articles.routes.js
├  ├── models/
├  ├── middlewares/
├  ├    ├──handleId.middleware.js
├  ├── app.js
├  ├── server.js
├──.gitignore
└── .env
```

-------------------

## 2. Required APIs

### A. View Adoptable Pets by City

- **Endpoint:** `GET /api/pets`
- **Query Type:** Query
- **Query Params:**
  - `city` (String) – Required

#### Example:
```http
GET /api/pets?city=Damascus
```

#### Response:
```json
[
  {
    "id": "1",
    "name": "Luna",
    "type": "Cat",
    "city": "Damascus",
    "available": true
  }
]
```

#### Possible Errors:
- Missing `city`: 400 Bad Request
- City not found: 404 Not Found

---------------

### B. Find Emergency Veterinary Clinics

- **Endpoint:** `GET /api/clinics/emergency`
- **Query Type:** Query
- **Query Params:**
  - `city` (String) – Required

#### Example:
```http
GET /api/clinics/emergency?city=Aleppo
```

#### Response:
```json
[
  {
    "name": "24H Vet Clinic",
    "address": "Main St, Aleppo",
    "isOpenNow": true
  }
]
```

#### Possible Errors:
- Missing `city`: 400 Bad Request
- No open clinics: 404 Not Found

-------------------------

### C. Search Articles by Pet Type

- **Endpoint:** `GET /api/articles`
- **Query Type:** Query
- **Query Params:**
  - `type` (String: dog, cat, etc.) – Required

#### Example:
```http
GET /api/articles?type=dog
```

#### Response:
```json
[
  {
    "title": "How to care for your dog",
    "content": "Feeding, hygiene, and training tips...",
    "type": "dog"
  }
]
```

#### Possible Errors:
- Missing `type`: 400 Bad Request
- Unsupported type: 404 Not Found


