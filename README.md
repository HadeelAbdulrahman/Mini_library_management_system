# 📚 Mini Library Management System

## 📌 Project Description

This project is a **Mini Library Management System** developed using **Django**.
It allows managing books and controlling the borrowing and returning process while enforcing **role-based authentication and authorization**.

The system clearly separates:

* 👨‍🎓 **Students**
* 🧑‍💼 **Staff**
* 👑 **Admins / Superusers**

Each role has **strictly isolated access** and **cannot access or interfere with the pages, authorities, or data of other roles**.

The project demonstrates:

* Django authentication and authorization
* Role-based access control using decorators
* REST-style backend endpoints
* Asynchronous frontend–backend communication using Fetch API
* Secure login flow without role-leak vulnerabilities

---

## 🛠️ Technologies Used

* **Backend:** Django (Python)
* **Database:** SQLite (default Django database)
* **Frontend:**

  * HTML (structure)
  * CSS (styling)
  * JavaScript (logic & DOM manipulation)
* **Authentication:** Django built-in authentication system
* **Authorization:** Custom role decorators
* **Communication:** Fetch API (async/await)

---

## ✨ Main Features

* 📖 Add, view, update, and delete books
* 🔄 Borrow and return books
* 🚫 Prevent borrowing unavailable books
* 🔐 Role-based dashboards (Student / Staff / Admin)
* ❌ Students cannot access staff or admin pages
* ❌ Staff cannot access student or admin pages
* ❌ Admins cannot access student or staff dashboards
* 👤 Unique usernames enforced
* ⏳ Asynchronous frontend–backend communication
* 🛡️ Server-side authorization (no template-only protection)

---

## 🔐 Authentication & Authorization Rules

| Role    | Access                  |
| ------- | ----------------------- |
| Student | Student dashboard only  |
| Staff   | Staff dashboard only    |
| Admin   | Django admin panel only |

* Admins **must login via `/admin/`**
* Students **cannot login using admin credentials**
* Authorization is enforced using **server-side decorators**
* Entry pages are public; dashboards are protected

---

## 📂 Project Structure (Simplified)

```
Mini_library_management_system/
│
├── library/
│   ├── views.py        # Business logic & access control
│   ├── decorators.py  # Role-based authorization
│   ├── urls.py        # App routing
│   ├── models.py      # Database models
│   └── templates/     # HTML templates
│
├── static/
│   ├── css/
│   └── js/
│
├── manage.py
└── db.sqlite3
```

---

## ⚙️ Recommended Execution Environment

To avoid **environment conflicts** (Python version, Django version, missing dependencies, or OS-specific issues), it is **highly recommended** to run this project using **GitHub Codespaces**.

### Why GitHub Codespaces?

* Provides a **consistent and controlled environment**
* Avoids local setup issues
* Eliminates Python and Django version conflicts
* Ideal for **testing, grading, and demonstrations**
* Runs directly in the browser

---

## ▶️ How to Run the Project (Using GitHub Codespaces – Recommended)

1. Open the project repository on GitHub
2. Click **Code → Codespaces → Create codespace**
3. Wait for the environment to initialize
4. Run the following commands:

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

5. Open the forwarded port provided by Codespaces

---

## ▶️ How to Run Locally (Optional)

> ⚠️ Local execution may cause environment conflicts.

1. Install Python 3.8+
2. Install Django:

```bash
pip install django
```

3. Apply migrations:

```bash
python manage.py makemigrations
python manage.py migrate
```

4. Create admin account:

```bash
python manage.py createsuperuser
```

5. Run server:

```bash
python manage.py runserver
```

---

## 🔁 Borrow & Return Workflow (Simple)

1. Student logs in
2. Student clicks **Borrow**
3. Backend checks availability
4. If available → book is borrowed
5. Available copies decrease
6. Student clicks **Return**
7. Book becomes available again

---

## 👤 Username Uniqueness

* All usernames are **unique**
* Enforced at:

  * Database level
  * Form validation level
* Duplicate usernames are automatically rejected with a clear message

---

## 🎯 Project Purpose

This project is intended for:

* Academic submission
* Learning Django authentication & authorization
* Understanding role-based access control
* Demonstrating secure backend logic
* Discussion and viva examinations

---

## ✅ Key Design Decisions

* Authorization handled **only on the server**
* No role logic inside templates
* No role-based redirects in public entry pages
* Django admin used as the **single admin access point**
* Clean separation between authentication and authorization
