# 📚 Online Library Management System (Django)

A web-based Library Management System built using Django. This project allows library admins to manage students, books, and book issuance efficiently, with a user-friendly interface and built-in authentication.

---

## 🚀 Features

- 👤 Admin Login & Dashboard  
- 📚 Add / Update / Delete Books  
- 🎓 Manage Student Information  
- 📖 Issue and Return Book Management  
- 🔍 Search & Filter Books  
- 🖼️ Upload Student Profile Photos  
- 🧾 Clean UI with Bootstrap and HTML templates  

---

## 🛠️ Tech Stack

| Technology     | Usage                                |
|----------------|----------------------------------------|
| Python 3.x     | Backend language                      |
| Django         | Web framework                         |
| SQLite         | Default database                      |
| HTML, CSS      | Templates and styling                 |
| Bootstrap      | Responsive design                     |
| Pillow         | Image uploads                         |

---

## ⚙️ Setup Instructions (Local)

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/library-management-system.git
cd library-management-system
```

### 2. Create & Activate Virtual Environment

```bash
python -m venv env
env\Scripts\activate       # On Windows
# OR
source env/bin/activate    # On Mac/Linux
```

### 3. Install Dependencies

```bash
pip install django pillow
```

> Optional: Generate your own `requirements.txt`
```bash
pip freeze > requirements.txt
```

### 4. Run Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Create Superuser (Admin Login)

```bash
python manage.py createsuperuser
```

### 6. Start Development Server

```bash
python manage.py runserver
```

Visit: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)  
Admin Panel: [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

---

## 📁 Project Structure

```
online-library-management-python-django/
│
├── manage.py
├── db.sqlite3
├── requirements.txt         # (Create if missing)
│
├── LibraryManagementSystem/ # Django settings project
│   ├── settings.py
│   └── urls.py
│
└── library/                 # Main Django app
    ├── models.py
    ├── views.py
    ├── urls.py
    ├── forms.py
    ├── admin.py
    ├── templates/
    ├── static/
    └── media/
```

---

## 📦 Requirements

If not included, create a `requirements.txt` manually:

```text
Django>=3.2
Pillow
```

---

## 🛡️ Admin Panel Branding

To customize admin branding, add this to `admin.py`:

```python
admin.site.site_header = "Library Admin Panel"
admin.site.site_title = "Library Management"
admin.site.index_title = "Welcome to Library Admin Dashboard"
```

---

## 📸 Screenshots (Optional)

> You can add screenshots in `static/images/` and link them here:

```markdown
![Dashboard](static/images/dashboard.png)
![Book List](static/images/booklist.png)
```

---

## 🙋 Author

- **V NAVNEETH**
- GitHub: [@your-Navneethoffcial](https://github.com/Navneethofficial)

---

## 📜 License

Open source for learning and development. Attribution appreciated.
