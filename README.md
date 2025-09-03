# Stroke Consultation System

A comprehensive Django-based web application designed to streamline stroke patient management and consultation workflows in hospital stroke units. This system provides role-based access control for medical technicians and neurologists, enabling efficient patient monitoring, consultation management, and critical alert systems.

## 🏥 Project Overview

The Stroke Consultation System is a specialized medical application that addresses the critical time-sensitive nature of stroke treatment. It provides healthcare professionals with tools to:

- **Monitor patient vitals** in real-time with automated alert systems
- **Track NIHSS scores** (National Institutes of Health Stroke Scale) for stroke severity assessment
- **Manage consultations** with comprehensive medical documentation
- **Handle lab results** and imaging studies for stroke diagnosis
- **Ensure TPA treatment window compliance** (4.5-hour window for ischemic stroke treatment)
- **Maintain patient records** with complete medical history and current medications

## 🚀 Key Features

### 🔐 Role-Based Access Control
- **Technician Role**: Patient registration, vital signs monitoring, basic patient management
- **Neurologist Role**: Full consultation capabilities, diagnosis, treatment planning, lab interpretation

### 📊 Patient Management
- **Comprehensive Patient Profiles**: Personal information, medical history, allergies, current medications
- **Vital Signs Tracking**: Blood pressure, heart rate, oxygen saturation, temperature, respiratory rate
- **NIHSS Score Monitoring**: Stroke severity assessment with automatic updates
- **Hospital ID Generation**: Automated unique identifier system (P-1001, P-1002, etc.)

### 🚨 Alert System
- **Critical Alerts**: Immediate notification for life-threatening conditions
- **Warning Alerts**: Important but non-critical patient status changes
- **Information Alerts**: General updates and reminders
- **Alert Acknowledgment**: Track who responded and when

### 🩺 Consultation Management
- **Symptom Onset Tracking**: Critical for TPA treatment window compliance
- **Diagnosis Documentation**: Comprehensive stroke assessment and classification
- **Treatment Planning**: Detailed therapeutic intervention strategies
- **Test Orders**: Lab work and imaging study requests

### 🔬 Medical Data Integration
- **Lab Results**: CBC, BMP, INR, PT, PTT values
- **Imaging Studies**: CT/MRI findings with stroke type classification
- **Recent Medical Events**: Surgery, trauma, previous strokes, myocardial infarction
- **Consent Management**: TPA treatment consent tracking

## 📁 Project Structure

```
Stroke-Consultation-System/
├── 📁 patientsystem/                    # Main Django application
│   ├── 📁 __init__.py
│   ├── 📁 __pycache__/
│   ├── 📁 management/                   # Custom management commands
│   │   └── 📁 commands/
│   ├── 📁 migrations/                   # Database migrations
│   │   ├── 📄 0001_initial.py
│   │   ├── 📄 0002_patient_vitals_alert_patient_vitals_consultation.py
│   │   ├── 📄 0003_patient_chief_complaint.py
│   │   ├── 📄 0004_patient_hospital_id_alter_userprofile_role.py
│   │   ├── 📄 0005_populate_hospital_ids.py
│   │   ├── 📄 0006_alter_patient_hospital_id.py
│   │   ├── 📄 0007_alert_acknowledged_alert_acknowledged_at_and_more.py
│   │   └── 📄 0008_consultation_symptom_onset_time_and_more.py
│   ├── 📁 templates/                    # HTML templates
│   │   ├── 📄 consultations.html
│   │   ├── 📄 dashboard.html
│   │   ├── 📄 new_consultation.html
│   │   ├── 📄 patient_detail.html
│   │   └── 📄 alerts.html
│   ├── 📄 __init__.py
│   ├── 📄 admin.py                      # Django admin configuration
│   ├── 📄 apps.py                       # App configuration
│   ├── 📄 decorators.py                 # Custom decorators for role-based access
│   ├── 📄 models.py                     # Database models (237 lines)
│   ├── 📄 signals.py                    # Django signals for automatic actions
│   ├── 📄 tests.py                      # Test suite
│   ├── 📄 urls.py                       # URL routing (16 lines)
│   └── 📄 views.py                      # View functions (466 lines)
├── 📁 stroke_unit_system/               # Django project settings
│   ├── 📄 __init__.py
│   ├── 📄 asgi.py                       # ASGI configuration
│   ├── 📄 production_settings.py         # Production environment settings
│   ├── 📄 urls.py                       # Main URL configuration
│   └── 📄 wsgi.py                       # WSGI configuration
├── 📁 templates/                         # Global templates
│   ├── 📁 registration/                 # Authentication templates
│   ├── 📄 base.html                     # Base template (118 lines)
│   ├── 📄 404.html                      # Error page (12 lines)
│   └── 📄 500.html                      # Server error page (12 lines)
├── 📁 static/                           # Static files (CSS, JS, images)
├── 📁 staticfiles/                      # Collected static files
├── 📄 .env                              # Environment variables (create this)
├── 📄 .gitignore                        # Git ignore patterns
├── 📄 db.sqlite3                        # SQLite database
├── 📄 manage.py                         # Django management script
├── 📄 requirements.txt                  # Python dependencies (7 packages)
├── 📄 seed_db.py                        # Database seeding script
├── 📄 seed.py                           # Alternative seeding script
├── 📄 setup.py                          # Project setup script
├── 📄 settings.py                       # Django settings (152 lines)
└── 📄 README.md                         # This file
```

## 🏗️ Technical Architecture

### Backend Framework
- **Django 5.0.2**: Modern Python web framework with robust ORM
- **SQLite Database**: Development database (configurable for production)
- **Custom User Profiles**: Extended user model with role-based permissions

### Data Models
- **Patient**: Core patient information and demographics
- **Vitals**: Real-time physiological measurements
- **Consultation**: Medical consultation records and assessments
- **Alert**: Critical notification system
- **LabResults**: Laboratory test outcomes
- **ImagingStudy**: Diagnostic imaging findings
- **RecentEvents**: Recent medical history
- **Consent**: Treatment consent documentation

### Security Features
- **Authentication Required**: All views require user login
- **Role-Based Decorators**: `@technician_required`, `@neurologist_required`
- **CSRF Protection**: Built-in Django security
- **Session Management**: Secure user session handling

## 🔌 API Endpoints

### Authentication & User Management
```
POST   /accounts/login/                   # User login
POST   /accounts/logout/                  # User logout
GET    /accounts/register/                # User registration
```

### Patient Management
```
GET    /patientsystem/                    # Dashboard (role-based)
POST   /patientsystem/patient/new/        # Create new patient
GET    /patientsystem/patient/<id>/       # Patient details
POST   /patientsystem/patient/<id>/edit_vitals/  # Update vitals
```

### Consultation Management
```
POST   /patientsystem/patient/<id>/consultation/new/  # New consultation
GET    /patientsystem/consultations/      # List consultations
```

### Alert System
```
GET    /patientsystem/alerts/             # List all alerts
POST   /patientsystem/alert/<id>/acknowledge/  # Acknowledge alert
```

## 🚀 Getting Started

### Prerequisites
- **Python**: 3.8+ (3.9+ recommended)
- **pip**: Latest version
- **Git**: For version control
- **Virtual Environment**: Python venv or conda
- **Database**: SQLite (development) or PostgreSQL (production)

### System Requirements
- **RAM**: Minimum 2GB, Recommended 4GB+
- **Storage**: Minimum 1GB free space
- **OS**: Windows 10+, macOS 10.14+, Ubuntu 18.04+
- **Browser**: Chrome 80+, Firefox 75+, Safari 13+

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/stroke-consultation-system.git
   cd stroke-consultation-system
   ```

2. **Create virtual environment**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Environment setup**
   ```bash
   # Create .env file
   cp .env.example .env
   
   # Edit .env with your settings
   nano .env  # or use your preferred editor
   ```

5. **Database setup**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

6. **Create superuser**
   ```bash
   python manage.py createsuperuser
   # Follow prompts to create admin account
   ```

7. **Load sample data (optional)**
   ```bash
   python manage.py shell
   from patientsystem.models import *
   # Sample data is automatically loaded
   exit()
   ```

8. **Run the development server**
   ```bash
   python manage.py runserver
   ```

9. **Access the application**
   - Open your browser and navigate to `http://127.0.0.1:8000`
   - Login with your superuser credentials
   - Navigate to `/admin/` to access Django admin

### Database Setup

The system includes sample data for demonstration:
- Sample patients with realistic medical profiles
- Pre-configured vital signs
- Example consultations and alerts

To populate with sample data:
```bash
python manage.py shell
from patientsystem.models import *
# Sample data is automatically loaded
```

## 👥 User Roles & Permissions

### Technician
- **Dashboard Access**: View all patients and their current status
- **Patient Management**: Add new patients, update basic information
- **Vital Signs**: Monitor and update patient vitals
- **Alert Monitoring**: View and acknowledge alerts

### Neurologist
- **Full Patient Access**: Complete patient history and current status
- **Consultation Creation**: New consultations with comprehensive medical assessment
- **Treatment Planning**: Diagnosis, treatment plans, and test orders
- **Lab Interpretation**: Review and document lab results
- **Imaging Review**: Document CT/MRI findings and stroke classification

## 📱 User Interface

### Dashboard Views
- **Technician Dashboard**: Patient list with vital signs overview
- **Neurologist Dashboard**: Patient list with active alerts and consultation tools

### Patient Management
- **Patient Detail View**: Comprehensive patient information display
- **Vital Signs Editor**: Real-time vital signs monitoring and updates
- **Consultation Forms**: Structured medical assessment documentation

### Alert System
- **Alert Dashboard**: Centralized alert management
- **Alert Acknowledgment**: Track response times and responsible staff

## 🔧 Configuration

### Environment Variables
Create a `.env` file in the project root:
```env
# Django Settings
SECRET_KEY=your-super-secret-key-here
DEBUG=False
ALLOWED_HOSTS=localhost,127.0.0.1,your-domain.com

# Database Settings
DATABASE_URL=postgresql://user:password@localhost:5432/stroke_db

# Security Settings
CSRF_TRUSTED_ORIGINS=https://your-domain.com
CSRF_COOKIE_SECURE=True
CSRF_COOKIE_HTTPONLY=True

# Email Settings (optional)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password
```

### Django Settings
Key configuration options in `settings.py`:
```python
# Security Settings
DEBUG = False  # Set to False in production
ALLOWED_HOSTS = ['your-domain.com', 'www.your-domain.com']

# Database Configuration
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'stroke_db',
        'USER': 'db_user',
        'PASSWORD': 'secure_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}

# Static Files
STATIC_ROOT = BASE_DIR / 'staticfiles'
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
```

### Production Deployment
The system is configured for production deployment with:
- **Render.com** compatibility (configured in settings)
- **PostgreSQL** database support
- **Gunicorn** WSGI server
- **WhiteNoise** static file serving

## 📊 Database Schema

### Core Relationships
```
Patient (1) ←→ (1) Vitals
Patient (1) ←→ (Many) Consultation
Consultation (1) ←→ (1) LabResults
Consultation (1) ←→ (1) ImagingStudy
Consultation (1) ←→ (1) Consent
Patient (1) ←→ (1) RecentEvents
```

### Key Fields
- **Patient**: hospital_id, demographics, medical history
- **Vitals**: physiological measurements with timestamp
- **Consultation**: medical assessment with NIHSS scoring
- **Alert**: notification system with acknowledgment tracking

### Database Migrations
Current migration history:
- `0001_initial.py`: Initial database setup
- `0002_patient_vitals_alert_patient_vitals_consultation.py`: Core models
- `0003_patient_chief_complaint.py`: Patient complaint tracking
- `0004_patient_hospital_id_alter_userprofile_role.py`: Hospital ID system
- `0005_populate_hospital_ids.py`: Data population
- `0006_alter_patient_hospital_id.py`: ID system refinement
- `0007_alert_acknowledged_alert_acknowledged_at_and_more.py`: Alert system
- `0008_consultation_symptom_onset_time_and_more.py`: Consultation enhancements

## 🚨 Critical Features

### TPA Treatment Window
- **4.5-Hour Window**: Automatic calculation from symptom onset
- **Time Tracking**: Precise symptom onset documentation
- **Treatment Eligibility**: Real-time assessment of treatment options

### NIHSS Scoring
- **Stroke Severity**: 0-42 scale assessment
- **Automatic Updates**: Score tracking across consultations
- **Treatment Guidance**: Score-based treatment recommendations

## 🚀 Deployment

### Local Development
```bash
# Development server
python manage.py runserver

# Run with specific port
python manage.py runserver 8080

# Run with specific host
python manage.py runserver 0.0.0.0:8000
```

### Production Deployment

#### Render.com Deployment
1. **Connect Repository**: Link your GitHub repo to Render
2. **Environment Variables**: Set all required environment variables
3. **Build Command**: `pip install -r requirements.txt`
4. **Start Command**: `gunicorn stroke_unit_system.wsgi:application`

#### Heroku Deployment
1. **Install Heroku CLI**: `brew install heroku/brew/heroku`
2. **Login**: `heroku login`
3. **Create App**: `heroku create your-app-name`
4. **Set Config**: `heroku config:set SECRET_KEY=your-key`
5. **Deploy**: `git push heroku main`

#### Docker Deployment
```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
EXPOSE 8000

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "stroke_unit_system.wsgi:application"]
```

### Environment-Specific Settings
```python
# production_settings.py
import os
from .settings import *

DEBUG = False
ALLOWED_HOSTS = ['your-domain.com']

# Database
import dj_database_url
DATABASES['default'] = dj_database_url.config()

# Static files
STATIC_ROOT = BASE_DIR / 'staticfiles'
STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'

# Security
SECURE_SSL_REDIRECT = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SECURE = True
```

## 🧪 Testing

### Running Tests
```bash
# Run all tests
python manage.py test

# Run specific app tests
python manage.py test patientsystem

# Run with coverage
coverage run --source='.' manage.py test
coverage report
coverage html  # Generate HTML report
```

### Test Structure
```
patientsystem/
├── tests.py              # Main test file
├── test_models.py        # Model tests
├── test_views.py         # View tests
└── test_forms.py         # Form tests
```

### Test Data
```python
# Example test data creation
from patientsystem.models import Patient, Vitals

def create_test_patient():
    vitals = Vitals.objects.create(
        blood_pressure="120/80",
        heart_rate=72,
        oxygen_saturation=98.0,
        temperature=36.8
    )
    return Patient.objects.create(
        first_name="Test",
        last_name="Patient",
        date_of_birth="1980-01-01",
        gender="M",
        vitals=vitals
    )
```

## 🔍 Monitoring & Logging

### Django Logging Configuration
```python
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'file': {
            'level': 'INFO',
            'class': 'logging.FileHandler',
            'filename': 'django.log',
        },
    },
    'loggers': {
        'django': {
            'handlers': ['file'],
            'level': 'INFO',
            'propagate': True,
        },
    },
}
```

### Health Checks
```python
# Add to urls.py
from django.http import HttpResponse

def health_check(request):
    return HttpResponse("OK", content_type="text/plain")

urlpatterns = [
    path('health/', health_check, name='health_check'),
    # ... other URLs
]
```

## 🚨 Troubleshooting

### Common Issues

#### Database Connection Errors
```bash
# Reset database
python manage.py flush
python manage.py migrate

# Check database status
python manage.py dbshell
```

#### Static Files Not Loading
```bash
# Collect static files
python manage.py collectstatic

# Check static files configuration
python manage.py findstatic --verbosity 2 css/style.css
```

#### Migration Issues
```bash
# Reset migrations
python manage.py migrate patientsystem zero
rm patientsystem/migrations/0*.py
python manage.py makemigrations
python manage.py migrate
```

#### Permission Errors
```bash
# Check file permissions
chmod 755 manage.py
chmod -R 755 patientsystem/

# Check user permissions
python manage.py check --deploy
```

### Performance Issues
```bash
# Database optimization
python manage.py dbshell
# Run EXPLAIN ANALYZE on slow queries

# Memory usage
python manage.py shell
import psutil
print(psutil.virtual_memory())
```

## 📈 Performance & Optimization

### Database Optimization
- **Indexing**: Add database indexes for frequently queried fields
- **Query Optimization**: Use `select_related()` and `prefetch_related()`
- **Connection Pooling**: Configure database connection pooling

### Caching Strategy
```python
# Redis caching configuration
CACHES = {
    'default': {
        'BACKEND': 'django_redis.cache.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/1',
        'OPTIONS': {
            'CLIENT_CLASS': 'django_redis.client.DefaultClient',
        }
    }
}
```

### Static File Optimization
- **Compression**: Enable gzip compression
- **CDN**: Use Content Delivery Network for static files
- **Caching**: Implement browser caching headers

## 🔒 Security Considerations

### Security Checklist
- [ ] `DEBUG = False` in production
- [ ] Strong `SECRET_KEY`
- [ ] HTTPS enabled
- [ ] CSRF protection active
- [ ] SQL injection prevention
- [ ] XSS protection
- [ ] Rate limiting implemented
- [ ] Input validation
- [ ] Output sanitization

### Security Headers
```python
# Add security middleware
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    # ... other middleware
]

# Security settings
SECURE_BROWSER_XSS_FILTER = True
SECURE_CONTENT_TYPE_NOSNIFF = True
X_FRAME_OPTIONS = 'DENY'
```

## 📚 API Documentation

### Authentication
All API endpoints require authentication. Include the session cookie or use Django's built-in authentication system.

### Request/Response Examples

#### Create Patient
```http
POST /patientsystem/patient/new/
Content-Type: application/x-www-form-urlencoded

first_name=John&last_name=Doe&date_of_birth=1980-01-01&gender=M
```

#### Update Vitals
```http
POST /patientsystem/patient/1/edit_vitals/
Content-Type: application/x-www-form-urlencoded

blood_pressure=120/80&heart_rate=72&oxygen_saturation=98.0&temperature=36.8
```

#### Create Consultation
```http
POST /patientsystem/patient/1/consultation/new/
Content-Type: application/x-www-form-urlencoded

diagnosis=Ischemic stroke&treatment_plan=TPA administration&nihss_score=8
```

## 🔄 Version History

### v1.0.0 (Current)
- Initial release with core functionality
- Role-based access control
- Patient management system
- Consultation tracking
- Alert system
- NIHSS scoring
- TPA treatment window tracking

### Planned Features
- Real-time notifications
- Mobile application
- Advanced analytics
- Telemedicine integration
- HL7 FHIR compliance

## 🤝 Contributing

### Development Setup
1. **Fork the repository**
2. **Create feature branch**: `git checkout -b feature/amazing-feature`
3. **Install development dependencies**:
   ```bash
   pip install -r requirements-dev.txt
   ```
4. **Run tests**: `python manage.py test`
5. **Make changes** and test thoroughly
6. **Commit changes**: `git commit -m 'Add amazing feature'`
7. **Push to branch**: `git push origin feature/amazing-feature'`
8. **Open Pull Request**

### Code Style
- Follow PEP 8 Python style guide
- Use meaningful variable and function names
- Add docstrings to all functions and classes
- Include type hints where appropriate

### Testing Requirements
- All new features must include tests
- Maintain 90%+ code coverage
- Run full test suite before submitting PR

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### Getting Help
- **GitHub Issues**: Create an issue for bugs or feature requests
- **Documentation**: Check Django documentation for technical questions
- **Community**: Join Django community forums

### Contact Information
- **Project Maintainer**: [Your Name]
- **Email**: [your-email@domain.com]
- **GitHub**: [@yourusername]

## 🏥 Medical Disclaimer

This software is designed to assist healthcare professionals in patient management and should not replace clinical judgment. Always verify critical medical decisions and follow established clinical protocols.

### Medical Compliance
- **HIPAA Compliance**: Ensure proper data handling and privacy
- **Clinical Validation**: Verify all medical calculations and algorithms
- **Professional Oversight**: Use under appropriate medical supervision

## 📊 System Requirements

### Minimum Requirements
- **Python**: 3.8+
- **RAM**: 2GB
- **Storage**: 1GB
- **Database**: SQLite (dev) / PostgreSQL (prod)

### Recommended Requirements
- **Python**: 3.9+
- **RAM**: 4GB+
- **Storage**: 5GB+
- **Database**: PostgreSQL 12+
- **Cache**: Redis 6+

### Browser Support
- **Chrome**: 80+
- **Firefox**: 75+
- **Safari**: 13+
- **Edge**: 80+

---

**Built with ❤️ for healthcare professionals working in stroke units**

*Last updated: December 2024*


