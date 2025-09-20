
# Jet2holidayz - Hotel Booking Platform

A comprehensive hotel booking platform built with Django, featuring modern UI/UX, secure payment processing, and complete booking management system.

## 🚀 Features

### Core Features
- **Advanced Hotel Search**: Search by location, dates, price range, amenities, and ratings
- **Real-time Booking**: Instant booking confirmation with email notifications
- **User Authentication**: Secure login/registration with role-based access
- **Payment Integration**: Secure payment processing with mock payment gateway
- **Review System**: User reviews and ratings for hotels with verification
- **Wishlist Management**: Save favorite hotels for quick access
- **Admin Dashboard**: Comprehensive management panel for hotel owners
- **Email Notifications**: Automated booking confirmations and reminders
- **Responsive Design**: Mobile-first responsive design for all devices
- **Search History**: Track user search patterns for better UX

### Technical Features
- **REST API**: Comprehensive API endpoints for mobile/web integration
- **Security**: Production-ready security features and HTTPS support
- **Performance**: Optimized queries and caching for fast response times
- **Scalability**: Modular architecture for easy scaling
- **Monitoring**: Comprehensive logging and error tracking
- **Multi-role Support**: Customer, Hotel Owner, and Admin role management

## 🛠️ Technology Stack

### Backend
- **Framework**: Django 4.2.7
- **Database**: SQLite (development) / PostgreSQL (production)
- **API**: Django REST Framework
- **Authentication**: Django built-in auth + Token authentication
- **Email**: SMTP with HTML templates
- **Forms**: Crispy Forms with Bootstrap 5 integration
- **Storage**: Local storage (development) / AWS S3 (production)

### Frontend
- **CSS Framework**: Bootstrap 5
- **JavaScript**: Vanilla JS with modern ES6+ features
- **Icons**: Font Awesome
- **Forms**: Crispy Forms with Bootstrap 5
- **Responsive**: Mobile-first design
- **UI Components**: Custom notification system and interactive elements

### DevOps & Deployment
- **Environment**: django-environ for configuration
- **Static Files**: Django static files with compression
- **Security**: HTTPS, HSTS, CSRF protection, rate limiting
- **Monitoring**: Django logging with file and console handlers

## 📁 Project Structure

```
booking-mvp/
├── backend/                 # Django project settings
│   ├── settings.py         # Main settings file
│   ├── urls.py             # Root URL configuration
│   └── wsgi.py             # WSGI application
├── hotels/                 # Hotels app
│   ├── models.py           # Hotel, Room, Booking models
│   ├── views.py            # Web and API views
│   ├── serializers.py      # DRF serializers
│   ├── urls.py             # Hotel URL patterns
│   ├── emails.py           # Email notification functions
│   └── admin.py            # Admin configurations
├── accounts/               # User accounts app
│   ├── models.py           # Custom User, Wishlist, SearchHistory models
│   ├── views.py            # Auth and profile views
│   ├── urls.py             # Account URL patterns
│   └── forms.py            # Authentication forms
├── reviews/                # Reviews & ratings app
│   ├── models.py           # Review model with verification
│   ├── views.py            # Review CRUD operations
│   ├── forms.py            # Review forms
│   ├── serializers.py      # Review API serializers
│   └── urls.py             # Review URL patterns
├── core/                   # Core utilities app
│   ├── models.py           # Site configuration model
│   ├── middleware.py       # Security middleware
│   ├── context_processors.py # Template context
│   ├── admin_views.py      # Admin dashboard views
│   └── views.py            # Utility views
├── templates/              # HTML templates
│   ├── base.html           # Base template
│   ├── home.html           # Homepage
│   ├── hotels/             # Hotel templates
│   ├── accounts/           # Auth templates
│   ├── reviews/            # Review templates
│   └── emails/             # Email templates
├── static/                 # Static files
│   ├── css/                # Custom CSS
│   ├── js/                 # Custom JavaScript
│   └── images/             # Images
├── staticfiles/            # Collected static files
├── media/                  # User uploaded files
├── requirements.txt        # Python dependencies
├── manage.py               # Django management script
├── create_sample_data.py   # Sample data creation script
├── create_superuser.py     # Superuser creation script
└── .env.example            # Environment variables template
```

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
   cp .env.example .env
   # Edit .env file with your configurations
   ```

5. **Database setup**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Create superuser**
   ```bash
   python manage.py createsuperuser
   # Or use the convenience script:
   python create_superuser.py
   ```

7. **Load sample data** (optional)
   ```bash
   python create_sample_data.py
   ```

8. **Collect static files**
   ```bash
   python manage.py collectstatic
   ```

9. **Run development server**
   ```bash
   python manage.py runserver
   ```

10. **Access the application**
    - Website: http://127.0.0.1:8000/
    - Admin: http://127.0.0.1:8000/admin/
    - API: http://127.0.0.1:8000/api/

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the project root:

```env
# Basic Configuration
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost,testserver

# Database (Production)
DB_NAME=jet2holidayz_db
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
DB_PORT=5432

# Email Configuration
EMAIL_BACKEND=django.core.mail.backends.smtp.EmailBackend
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-email-password
DEFAULT_FROM_EMAIL=Jet2holidayz <noreply@jet2holidayz.com>

# Site Configuration
SITE_NAME=Jet2holidayz
BASE_URL=https://yourdomain.com
SUPPORT_EMAIL=support@jet2holidayz.com
ADMIN_URL=secure-admin-panel/

# AWS S3 (Production)
AWS_ACCESS_KEY_ID=your-aws-access-key
AWS_SECRET_ACCESS_KEY=your-aws-secret-key
AWS_STORAGE_BUCKET_NAME=your-bucket-name
AWS_S3_REGION_NAME=us-east-1

# Security (Production)
SECURE_SSL_REDIRECT=True
SECURE_HSTS_SECONDS=31536000
SECURE_HSTS_INCLUDE_SUBDOMAINS=True
SECURE_HSTS_PRELOAD=True

# Payment Gateway (Stripe)
STRIPE_PUBLISHABLE_KEY=pk_test_51234567890
STRIPE_SECRET_KEY=sk_test_51234567890

# Redis/Celery (Optional)
REDIS_URL=redis://127.0.0.1:6379/1
CELERY_BROKER_URL=redis://127.0.0.1:6379/0
CELERY_RESULT_BACKEND=redis://127.0.0.1:6379/0
```

## 📚 API Documentation

### Authentication

All API endpoints support both Token and Session authentication.

**Get Token:**
```bash
POST /api-auth/token/
{
    "username": "your_username",
    "password": "your_password"
}
```

**Use Token:**
```bash
Authorization: Token your_token_here
```

### Core Endpoints

#### Hotels
- `GET /api/hotels/` - List all hotels with pagination
- `GET /api/hotels/{id}/` - Get hotel details
- `GET /api/hotels/featured/` - Get featured hotels
- `GET /api/hotels/search/` - Advanced hotel search with filters
- `GET /api/hotels/{id}/rooms/` - Get available rooms for a hotel

#### Bookings
- `GET /api/bookings/` - List user bookings
- `POST /api/bookings/` - Create new booking
- `GET /api/bookings/{id}/` - Get booking details
- `POST /api/bookings/{id}/cancel/` - Cancel booking
- `GET /api/bookings/upcoming/` - Get upcoming bookings
- `GET /api/bookings/history/` - Get booking history

#### Reviews
- `GET /api/reviews/` - List reviews
- `POST /api/reviews/` - Create new review (verified bookings only)
- `GET /api/reviews/{id}/` - Get review details
- `POST /api/reviews/{id}/helpful/` - Mark review as helpful

#### User Features
- `GET /api/wishlist/` - Get user wishlist
- `POST /api/wishlist/add/` - Add hotel to wishlist
- `DELETE /api/wishlist/remove/{hotel_id}/` - Remove from wishlist
- `GET /api/search-history/` - Get user search history

#### Cities & Amenities
- `GET /api/cities/` - List all cities
- `GET /api/amenities/` - List all amenities

### API Examples

**Search Hotels:**
```bash
GET /api/hotels/search/?location=New York&check_in=2024-01-15&check_out=2024-01-20&guests=2&price_min=100&price_max=500
```

**Create Booking:**
```bash
POST /api/bookings/
{
    "hotel": 1,
    "room": 1,
    "check_in": "2024-01-15",
    "check_out": "2024-01-20",
    "guests": 2,
    "special_requests": "Late check-in"
}
```

**Add Review:**
```bash
POST /api/reviews/
{
    "hotel": 1,
    "booking": 123,
    "overall_rating": 5,
    "cleanliness_rating": 5,
    "service_rating": 4,
    "location_rating": 5,
    "value_rating": 4,
    "comment": "Excellent stay with great service!"
}
```

## 🎨 Frontend Features

### User Interface
- **Modern Design**: Clean, professional design with Jet2holidayz branding
- **Responsive Layout**: Mobile-first responsive design
- **Interactive Elements**: Smooth animations and transitions
- **Form Validation**: Client-side validation with user feedback
- **Loading States**: Loading indicators for better UX
- **Notification System**: Toast notifications for user actions

### Key Pages
1. **Homepage**: Hero section, search form, featured hotels
2. **Hotel Search**: Advanced filters, sorting, pagination
3. **Hotel Details**: Image gallery, amenities, booking form, reviews
4. **User Dashboard**: Booking management, profile settings, wishlist
5. **Hotel Owner Dashboard**: Property management, analytics, bookings
6. **Review System**: Rating and review functionality with verification
7. **Admin Panel**: Comprehensive site administration

### JavaScript Features
- **AJAX Forms**: Form submissions without page reload
- **Dynamic Content**: Real-time price calculations and availability
- **Interactive Elements**: Hotel galleries, date pickers, filters
- **Wishlist Management**: Add/remove favorites with instant feedback
- **Search Suggestions**: Dynamic search suggestions and autocomplete
- **Notification System**: Custom toast notification system

## 🔒 Security Features

### Authentication & Authorization
- **Secure Password Hashing**: bcrypt password hashing
- **Session Security**: Secure session configuration
- **CSRF Protection**: CSRF tokens on all forms
- **Rate Limiting**: API and login rate limiting
- **User Permissions**: Role-based access control (Customer, Hotel Owner, Admin)
- **Booking Verification**: Review system requires verified bookings

### Production Security
- **HTTPS Enforcement**: Automatic HTTPS redirect
- **Security Headers**: Comprehensive security headers
- **Content Security Policy**: CSP headers for XSS protection
- **HSTS**: HTTP Strict Transport Security
- **Secure Cookies**: Secure and HttpOnly cookie flags
- **Input Validation**: Comprehensive form and API validation

### Monitoring & Logging
- **Security Logging**: Failed login attempts and suspicious activity
- **Error Tracking**: Comprehensive error logging
- **Access Logs**: Request logging for sensitive endpoints
- **Performance Monitoring**: Database query optimization

## 📧 Email System

### Email Templates
- **Booking Confirmation**: Detailed booking information with hotel details
- **Welcome Email**: New user onboarding with platform features
- **Cancellation Notice**: Booking cancellation confirmation
- **Check-in/Check-out Reminders**: Automated reminders for upcoming stays
- **Hotel Owner Notifications**: New booking and cancellation alerts

### Email Features
- **HTML Templates**: Beautiful responsive email templates
- **Automatic Sending**: Triggered by user actions
- **Error Handling**: Graceful fallback for email failures
- **SMTP Support**: Compatible with all major email providers
- **Template Variables**: Dynamic content with booking and user data

## 🏗️ Development

### Phase Implementation Status

#### Phase 1 (Core MVP) - ✅ Complete
- User authentication and authorization
- Hotel listing and search functionality
- Basic booking system
- Email notification system
- Admin interface
- Responsive web design

#### Phase 2 (Enhanced Features) - ✅ Complete
- Advanced search and filtering
- User reviews and ratings system
- Wishlist functionality
- Enhanced user experience
- Hotel owner dashboard
- Search history tracking

#### Phase 3 (Advanced Features) - 🚧 Planned
- Real payment gateway integration
- Advanced analytics and reporting
- Mobile app API optimization
- Multi-language support
- Advanced notification system

### Adding New Features

1. **Create Models** in appropriate app
2. **Run Migrations** to update database
3. **Create Serializers** for API endpoints
4. **Implement Views** for web and API
5. **Add URL Patterns** to route requests
6. **Create Templates** for web interface
7. **Write Tests** for functionality
8. **Update Documentation**

### Code Style
- **PEP 8**: Follow Python style guidelines
- **Django Conventions**: Use Django best practices
- **Crispy Forms**: Use crispy forms for form rendering
- **Documentation**: Comment complex logic
- **Testing**: Write tests for new features

### Database Migrations
```bash
# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Check migration status
python manage.py showmigrations

# Check for issues
python manage.py check
```

## 🚀 Deployment

### Production Checklist

- [ ] Set `DEBUG = False`
- [ ] Configure production database (PostgreSQL)
- [ ] Set up email service (SMTP)
- [ ] Configure static file serving
- [ ] Set up media file storage (AWS S3)
- [ ] Configure domain and HTTPS
- [ ] Set security environment variables
- [ ] Run security checks
- [ ] Set up monitoring and logging
- [ ] Configure backup strategy
- [ ] Test payment gateway integration
- [ ] Set up SSL certificates

### Deployment Steps

1. **Server Setup**
   ```bash
   # Install dependencies
   sudo apt update
   sudo apt install python3 python3-pip nginx postgresql redis-server
   ```

2. **Database Setup**
   ```bash
   # Create PostgreSQL database
   sudo -u postgres createdb jet2holidayz_db
   sudo -u postgres createuser --interactive
   ```

3. **Application Deployment**
   ```bash
   # Clone repository
   git clone <repository-url>
   cd booking-mvp
   
   # Install dependencies
   pip install -r requirements.txt
   
   # Configure environment
   cp .env.example .env
   # Edit .env with production values
   
   # Run migrations
   python manage.py migrate
   python manage.py collectstatic --noinput
   ```

4. **Web Server Configuration**
   ```nginx
   # Nginx configuration
   server {
       listen 80;
       server_name yourdomain.com;
       
       location /static/ {
           alias /path/to/booking-mvp/staticfiles/;
       }
       
       location /media/ {
           alias /path/to/booking-mvp/media/;
       }
       
       location / {
           proxy_pass http://127.0.0.1:8000;
           proxy_set_header Host $host;
           proxy_set_header X-Real-IP $remote_addr;
           proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
           proxy_set_header X-Forwarded-Proto $scheme;
       }
   }
   ```

### Health Monitoring

The application includes health check endpoints:
- **System Status**: Check overall system health
- **Database Connectivity**: Verify database connection
- **API Endpoints**: Test critical API functionality
- **Email System**: Verify email configuration

## 🧪 Testing

### Running Tests
```bash
# Run all tests
python manage.py test

# Run specific app tests
python manage.py test hotels
python manage.py test accounts
python manage.py test reviews

# Run with coverage
coverage run --source='.' manage.py test
coverage report
coverage html
```

### Test Types
- **Unit Tests**: Individual function testing
- **Integration Tests**: Feature workflow testing
- **API Tests**: Endpoint functionality testing
- **Frontend Tests**: User interface testing
- **Email Tests**: Email notification testing

## 📈 Features Overview

### For Customers
- Browse and search hotels with advanced filters
- View detailed hotel information and photos
- Read and write verified reviews
- Make secure bookings with instant confirmation
- Manage bookings and view history
- Save favorite hotels to wishlist
- Receive email confirmations and reminders

### For Hotel Owners
- Manage hotel listings and room inventory
- View booking analytics and reports
- Respond to customer reviews
- Manage pricing and availability
- Track revenue and occupancy rates
- Receive booking notifications

### For Administrators
- Comprehensive site management
- User and hotel moderation
- Review management and verification
- System analytics and reporting
- Email template management
- Security monitoring

## 📞 Support

### Getting Help
- **Documentation**: Check this README and inline code comments
- **Issues**: Create GitHub issues for bugs and feature requests
- **Discussions**: Use GitHub discussions for questions
- **Email**: Contact support@jet2holidayz.com

### Contributing
1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Make changes with tests
4. Commit changes (`git commit -m 'Add amazing feature'`)
5. Push to branch (`git push origin feature/amazing-feature`)
6. Submit pull request
7. Follow code review process

### Development Guidelines
- Follow Django best practices and conventions
- Write comprehensive tests for new features
- Use crispy forms for form rendering
- Ensure URL pattern consistency
- Update documentation for new features

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Django community for the excellent framework
- Django REST Framework for powerful API capabilities
- Bootstrap team for the responsive CSS framework
- Font Awesome for the beautiful icons
- Crispy Forms for elegant form rendering
- All contributors and testers

---

**Jet2holidayz** - Your trusted partner for seamless hotel booking experiences! 🏨✨

### Quick Links
- [Live Demo](http://127.0.0.1:8000/) (Development)
- [API Documentation](http://127.0.0.1:8000/api/)
- [Admin Panel](http://127.0.0.1:8000/admin/)
- [Support](mailto:support@jet2holidayz.com)
```



