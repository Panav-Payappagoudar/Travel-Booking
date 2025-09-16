

````markdown
# 🏨 BookingMVP - Hotel Booking Platform

A comprehensive Django-based hotel booking platform with modern UI/UX, built as a minimum viable product (MVP) for hotel reservation management.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Django](https://img.shields.io/badge/Django-4.2.7-green.svg)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.2-purple.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 🌟 Features

### 🏠 **Core Functionality**
- **Hotel Search & Browsing**: Advanced search with filters (location, price, amenities, ratings)  
- **User Authentication**: Registration, login, password management  
- **Booking System**: Complete reservation workflow with confirmation  
- **User Dashboard**: Booking history, profile management, wishlist  
- **Admin Panel**: Comprehensive hotel and booking management  
- **Responsive Design**: Mobile-first design with Bootstrap 5  

### 🔧 **Technical Features**
- **REST API**: Full API endpoints for all major operations  
- **Security**: CSRF protection, secure sessions, input validation  
- **Database**: SQLite (development) / PostgreSQL (production) support  
- **Static Files**: Optimized CSS/JS serving with CDN integration  
- **Email System**: Booking confirmations and notifications  
- **Media Handling**: Image upload and processing for hotels  

### 👥 **User Types**
- **Customers**: Browse hotels, make bookings, manage profile  
- **Hotel Owners**: Manage hotel listings, view bookings, analytics  
- **Administrators**: Full system management and oversight  

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+  
- pip (Python package manager)  
- Git  

### Installation

1. **Clone the repository**
    ```bash
    git clone <repository-url>
    cd booking-mvp
    ```

2. **Create virtual environment**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

4. **Environment setup**
    ```bash
    cp .env.example .env  # Create environment file
    # Edit .env with your settings
    ```

5. **Database setup**
    ```bash
    python manage.py migrate
    python manage.py createsuperuser  # Create admin account
    ```

6. **Collect static files**
    ```bash
    python manage.py collectstatic
    ```

7. **Run development server**
    ```bash
    python manage.py runserver
    ```

> Visit [http://127.0.0.1:8000](http://127.0.0.1:8000) to access the application.

---

## 📁 Project Structure

```text
booking-mvp/
├── accounts/           # User authentication & profiles
│   ├── models.py      # Custom User model
│   ├── views.py       # Auth views (login, register, dashboard)
│   ├── urls.py        # Account-related URLs
│   └── serializers.py # API serializers
├── hotels/            # Hotel & booking management
│   ├── models.py      # Hotel, Room, Booking models
│   ├── views.py       # Hotel search, booking views
│   ├── urls.py        # Hotel-related URLs
│   └── emails.py      # Email notifications
├── reviews/           # Hotel review system
├── core/              # Core functionality
│   ├── models.py      # Site settings
│   └── context_processors.py
├── templates/         # HTML templates
│   ├── accounts/      # User-related templates
│   ├── hotels/        # Hotel & booking templates
│   ├── includes/      # Reusable components
│   └── base.html      # Base template
├── static/            # Static files (CSS, JS, images)
│   ├── css/           # Custom stylesheets
│   └── js/            # Custom JavaScript
├── backend/           # Django project settings
│   ├── settings.py    # Main configuration
│   ├── urls.py        # Root URL configuration
│   └── wsgi.py        # WSGI configuration
├── manage.py          # Django management script
└── requirements.txt   # Python dependencies
````

---

## 🔧 Configuration

### Environment Variables (`.env`)

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost

# Database (Production)
DB_NAME=booking_mvp
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
DB_PORT=5432

# Email Configuration
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password

# Site Configuration
SITE_NAME=BookingMVP
BASE_URL=http://localhost:8000
```

---

## 🗄️ Database Models

### Core Models

* **User**: Extended Django user with profile fields
* **Hotel**: Hotel information, location, amenities
* **Room**: Room types, pricing, availability
* **Booking**: Reservation details, status tracking
* **Review**: User reviews and ratings
* **City**: Location data for hotels

### Key Relationships

* User → Bookings (One-to-Many)
* Hotel → Rooms (One-to-Many)
* Hotel → Bookings (One-to-Many)
* User → Reviews (One-to-Many)

---

## 🎨 Frontend Technologies

* **Bootstrap 5.3.2**: Responsive CSS framework
* **Font Awesome 6.4.0**: Icon library
* **Google Fonts (Inter)**: Typography
* **Custom CSS**: Brand-specific styling
* **Vanilla JavaScript**: Interactive functionality

---

## 🔌 API Endpoints

### Authentication

* `POST /accounts/api/register/` – User registration
* `POST /accounts/api/login/` – User login
* `POST /accounts/api/logout/` – User logout
* `GET /accounts/api/profile/` – Get user profile

### Hotels

* `GET /hotels/api/hotels/` – List hotels with filters
* `GET /hotels/api/hotels/{id}/` – Hotel details
* `GET /hotels/api/cities/` – List cities
* `GET /hotels/api/amenities/` – List amenities

### Bookings

* `GET /hotels/api/bookings/` – User bookings
* `POST /hotels/api/bookings/` – Create booking
* `PUT /hotels/api/bookings/{id}/` – Update booking
* `POST /hotels/api/bookings/{id}/cancel/` – Cancel booking

---

## 🧪 Testing

### Run Tests

```bash
python manage.py test
```

### Health Check

```bash
python manage.py check
python manage.py check --deploy  # Production checks
```

---

## 🚀 Deployment

### Production Setup

**Environment Configuration**

```bash
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
```

**Database Migration**

```bash
python manage.py migrate --settings=backend.settings
```

**Static Files**

```bash
python manage.py collectstatic --noinput
```

### Security Checklist

* Set strong `SECRET_KEY`
* Configure HTTPS settings
* Set up proper database credentials
* Configure email backend
* Set up media file storage (AWS S3 recommended)

### Docker Deployment (Optional)

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

---

## 🔒 Security Features

* CSRF Protection: Built-in Django CSRF middleware
* Session Security: Secure session handling
* Input Validation: Form and API input validation
* SQL Injection Protection: Django ORM prevents SQL injection
* XSS Protection: Template auto-escaping
* File Upload Security: File type and size restrictions
* Rate Limiting: API rate limiting (configurable)

---

## 📊 Performance Optimization

* Database Indexing: Optimized database queries
* Static File Compression: Minified CSS/JS
* Image Optimization: Automatic image processing
* Caching: Redis/Memcached support (configurable)
* CDN Integration: Bootstrap and Font Awesome from CDN

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch:

   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit changes:

   ```bash
   git commit -m 'Add amazing feature'
   ```
4. Push to branch:

   ```bash
   git push origin feature/amazing-feature
   ```
5. Open Pull Request

### Development Guidelines

* Follow PEP 8 for Python code
* Use meaningful commit messages
* Add tests for new features
* Update documentation as needed

---

## 📝 License

This project is licensed under the **MIT License** – see the LICENSE file for details.

---

## 🆘 Support

### Getting Help

* **Documentation**: Check this README and inline code comments
* **Issues**: Create GitHub issues for bugs or feature requests
* **Discussions**: Use GitHub discussions for questions

### Common Issues

* Database errors: Run `python manage.py migrate`
* Static files not loading: Run `python manage.py collectstatic`
* Permission errors: Check file permissions and virtual environment
* Import errors: Ensure all dependencies are installed

---

## 🚧 Roadmap

### Upcoming Features

* Payment integration (Stripe)
* Advanced search filters
* Real-time booking availability
* Mobile app API
* Multi-language support
* Hotel owner analytics dashboard
* Automated testing suite
* Docker containerization

### Version History

* **v1.0.0**: Initial MVP release with core booking functionality
* **v0.9.0**: Beta version with basic hotel management
* **v0.5.0**: Alpha version with user authentication

---

> **BookingMVP – Built with ❤️ using Django and Bootstrap**

```

---

✅ Developed by Panav Payappagoudar for SIH'25 , it is just my part that i contributed to the team.
```
