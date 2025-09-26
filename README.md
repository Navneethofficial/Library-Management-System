# Online Library Management System

A comprehensive web-based library management system built with Django 3.1 framework that enables efficient management of library resources, student accounts, and book transactions with role-based access control.

## 🚀 Features

### Student Features
- **Student Registration**: Complete registration with profile image upload
- **Secure Login System**: Authentication with role validation
- **Profile Management**: View and edit personal information including:
  - Contact details (email, phone)
  - Academic info (branch, classroom, roll number)
  - Profile image upload
- **Password Management**: Secure password change functionality
- **Book History**: View currently issued books with:
  - Book details (name, author)
  - Issue and expiry dates
  - Fine calculation for overdue books
- **Fine Tracking**: Automatic fine calculation (₹5 per day after 14-day period)

### Administrator Features
- **Admin Login**: Separate secure admin authentication
- **Book Management**:
  - Add new books with details (name, author, ISBN, category)
  - View all books in the library
  - Delete books from inventory
- **Student Management**:
  - View all registered students
  - Delete student accounts
  - Access student academic and contact information
- **Book Issuing System**:
  - Issue books to students using forms
  - Track issued books with automatic date management
  - View all currently issued books
- **Fine Management**: Automatic calculation and tracking of overdue fines
- **Comprehensive Dashboard**: Access to all administrative functions

## 🛠️ Technology Stack

- **Backend**: Django 3.1
- **Database**: SQLite3 (development)
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap
- **Authentication**: Django's built-in authentication system
- **File Handling**: Django's file upload system for profile images

## 📊 Database Models

### Book Model
- `name`: CharField (max_length=200)
- `author`: CharField (max_length=200) 
- `isbn`: PositiveIntegerField
- `category`: CharField (max_length=50)

### Student Model
- `user`: OneToOneField with Django User model
- `classroom`: CharField (max_length=10)
- `branch`: CharField (max_length=10)
- `roll_no`: CharField (max_length=3)
- `phone`: CharField (max_length=10)
- `image`: ImageField for profile pictures

### IssuedBook Model
- `student_id`: CharField (max_length=100)
- `isbn`: CharField (max_length=13)
- `issued_date`: DateField (auto_now=True)
- `expiry_date`: DateField (default=14 days from issue)

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

- Python 3.8 or higher
- pip (Python package installer)
- Virtual environment (recommended)

## ⚡ Installation & Setup

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd online-library-management-django
```

### 2. Create Virtual Environment
```bash
python -m venv library_env
source library_env/bin/activate  # On Windows: library_env\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install django
pip install Pillow  # For image handling
```

### 4. Database Setup
```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Create Superuser (Admin)
```bash
python manage.py createsuperuser
```

### 6. Run Development Server
```bash
python manage.py runserver
```

The application will be available at `http://127.0.0.1:8000/`

## 📁 Project Structure

```
LibraryManagementSystem/
│
├── LibraryManagementSystem/     # Main project directory
│   ├── __init__.py
│   ├── settings.py             # Project settings
│   ├── urls.py                 # Main URL configuration
│   ├── wsgi.py                 # WSGI configuration
│   └── asgi.py                 # ASGI configuration
│
├── library/                    # Main application
│   ├── migrations/             # Database migrations
│   ├── static/                 # Static files (CSS, JS, images)
│   ├── templates/              # HTML templates
│   ├── media/                  # User uploaded files
│   ├── __init__.py
│   ├── admin.py               # Admin panel configuration
│   ├── apps.py                # App configuration
│   ├── models.py              # Database models
│   ├── views.py               # View functions
│   ├── urls.py                # App URL patterns
│   └── forms.py               # Django forms
│
├── db.sqlite3                 # SQLite database file
├── manage.py                  # Django management script
└── README.md                  # Project documentation
```

## 🎯 Usage

### For Students:
1. **Registration**: Create account at `/student_registration/` with academic details
2. **Login**: Access account at `/student_login/`
3. **Profile**: View profile at `/profile/` and edit at `/edit_profile/`
4. **Books**: Check issued books and fines at `/student_issued_books/`
5. **Password**: Change password at `/change_password/`

### For Administrators:
1. **Admin Login**: Access admin panel at `/admin_login/`
2. **Add Books**: Add new books at `/add_book/`
3. **Manage Books**: View all books at `/view_books/`
4. **Manage Students**: View all students at `/view_students/`
5. **Issue Books**: Issue books to students at `/issue_book/`
6. **Track Issues**: View all issued books at `/view_issued_book/`

## 🔧 Configuration

### Media Files Configuration
The project is configured to handle file uploads:

```python
MEDIA_ROOT = os.path.join(BASE_DIR, 'library/media')
MEDIA_URL = '/media/'
```

### Static Files Configuration
```python
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "library/static")
]
```

### Template Configuration
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ["library/templates"],
        # ... other settings
    },
]
```

## 📊 API Endpoints

| Endpoint | Method | Description | Access Level |
|----------|--------|-------------|--------------|
| `/` | GET | Home page | Public |
| `/student_registration/` | GET, POST | Student registration | Public |
| `/student_login/` | GET, POST | Student login | Public |
| `/admin_login/` | GET, POST | Admin login | Public |
| `/logout/` | POST | User logout | Authenticated |
| `/profile/` | GET | Student profile view | Student |
| `/edit_profile/` | GET, POST | Edit student profile | Student |
| `/change_password/` | GET, POST | Change password | Student |
| `/student_issued_books/` | GET | View issued books | Student |
| `/add_book/` | GET, POST | Add new book | Admin |
| `/view_books/` | GET | View all books | Admin |
| `/view_students/` | GET | View all students | Admin |
| `/issue_book/` | GET, POST | Issue book to student | Admin |
| `/view_issued_book/` | GET | View all issued books | Admin |
| `/delete_book/<int:myid>/` | GET | Delete book | Admin |
| `/delete_student/<int:myid>/` | GET | Delete student | Admin |

## 🔒 Security Features

- **Role-based Access Control**: Separate login systems for students and administrators
- **Login Required Decorators**: Protected routes with authentication checks
- **CSRF Protection**: Built-in Django CSRF middleware
- **Password Validation**: Django's built-in password validators
- **Secure File Uploads**: Proper handling of profile image uploads
- **SQL Injection Prevention**: Django ORM protection
- **XSS Protection**: Django's built-in template system protection

## 🧮 Fine Calculation System

The system implements an automatic fine calculation:
- **Grace Period**: 14 days from issue date
- **Fine Rate**: ₹5 per day after grace period
- **Calculation**: `fine = (current_date - issue_date - 14_days) * 5`
- **Real-time Tracking**: Fines calculated dynamically on each view

## 🐛 Troubleshooting

### Common Issues:

1. **Migration Errors**:
   ```bash
   python manage.py makemigrations library
   python manage.py migrate
   ```

2. **Static Files Not Loading**:
   ```bash
   python manage.py collectstatic
   ```

3. **Image Upload Issues**:
   - Ensure Pillow is installed: `pip install Pillow`
   - Check media directory permissions

4. **Database Issues**:
   - Delete `db.sqlite3` and run migrations again
   - Check for model field conflicts

## 🚀 Deployment

### For Production:

1. **Update Settings**:
   ```python
   DEBUG = False
   ALLOWED_HOSTS = ['yourdomain.com']
   ```

2. **Environment Variables**:
   ```python
   import os
   SECRET_KEY = os.environ.get('SECRET_KEY')
   ```

3. **Database Configuration** (PostgreSQL):
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'library_db',
           'USER': 'your_username',
           'PASSWORD': 'your_password',
           'HOST': 'localhost',
           'PORT': '5432',
       }
   }
   ```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit changes (`git commit -am 'Add new feature'`)
4. Push to branch (`git push origin feature/new-feature`)
5. Create Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Django Documentation
- Bootstrap Framework
- FontAwesome Icons
- Stack Overflow Community

## ❤️ Made with Love

Built with ❤️ using Django Framework

---

**Note**: This is an educational project demonstrating Django web development concepts. For production use, additional security measures and optimizations should be implemented.
