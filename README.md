# Car Dealership Review Platform

A full-stack web application for car dealership management and customer reviews, built with Django, Express.js, MongoDB, and sentiment analysis.

![Build Status](https://github.com/jagrutisupe/fullstack-car-dealership/workflows/Django%20CI/badge.svg)
![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![Django Version](https://img.shields.io/badge/django-4.0%2B-green)
![Node Version](https://img.shields.io/badge/node-14%2B-brightgreen)

## 🚗 Project Overview

This application allows users to browse car dealerships, view reviews, and submit their own reviews with sentiment analysis. The platform integrates multiple services including a Django web application, Express/MongoDB microservice, and a sentiment analysis API.

## ✨ Features

- **User Authentication**: Secure login, logout, and registration system
- **Dealership Management**: Browse and filter dealerships by location
- **Review System**: Submit and view customer reviews for dealerships
- **Sentiment Analysis**: Automatic sentiment detection for reviews (positive/negative/neutral)
- **Admin Panel**: Manage car makes, models, and dealership data
- **Responsive Design**: Mobile-friendly interface
- **RESTful API**: Express.js microservice for dealer and review data
- **CI/CD Pipeline**: Automated testing and deployment

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                  Django Web App                      │
│  (Frontend, Views, Authentication, Templates)        │
└──────────────────┬──────────────────────────────────┘
                   │
         ┌─────────┴─────────┐
         │                   │
┌────────▼────────┐  ┌──────▼───────────┐
│  Express API    │  │  Sentiment API   │
│  (Node.js +     │  │  (Python Flask + │
│   MongoDB)      │  │   TextBlob)      │
└─────────────────┘  └──────────────────┘
```

## 🛠️ Technology Stack

### Backend
- **Django 4.x** - Web framework
- **Python 3.8+** - Programming language
- **Express.js** - RESTful API microservice
- **Node.js 14+** - JavaScript runtime
- **MongoDB** - NoSQL database for dealers and reviews
- **SQLite/PostgreSQL** - Django database

### Frontend
- **HTML5/CSS3** - Markup and styling
- **Bootstrap 5** - UI framework
- **JavaScript** - Client-side interactions

### Additional Services
- **Flask** - Sentiment analysis API
- **TextBlob** - Natural language processing
- **GitHub Actions** - CI/CD pipeline

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.8 or higher
- Node.js 14 or higher
- MongoDB 4.4 or higher
- Git
- pip (Python package manager)
- npm (Node package manager)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
```

### 2. Set Up Django Application

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Collect static files
python manage.py collectstatic
```

### 3. Set Up Express Microservice

```bash
# Navigate to Express directory
cd server

# Install dependencies
npm install

# Start MongoDB (in a separate terminal)
mongod

# Seed database (optional)
node seed.js

# Start Express server
node server.js
```

### 4. Set Up Sentiment Analysis Service

```bash
# Navigate to sentiment analyzer directory
cd sentiment_analyzer

# Install dependencies
pip install flask textblob

# Start sentiment service
python sentiment_analyzer.py
```

## 🎮 Running the Application

1. **Start MongoDB** (if not already running):
   ```bash
   mongod
   ```

2. **Start Express API** (Terminal 1):
   ```bash
   cd server
   node server.js
   # Runs on http://localhost:3000
   ```

3. **Start Sentiment Analyzer** (Terminal 2):
   ```bash
   cd sentiment_analyzer
   python sentiment_analyzer.py
   # Runs on http://localhost:5000
   ```

4. **Start Django Server** (Terminal 3):
   ```bash
   python manage.py runserver
   # Runs on http://localhost:8000
   ```

5. **Access the Application**:
   - Main App: http://localhost:8000
   - Admin Panel: http://localhost:8000/admin
   - API Endpoints: http://localhost:3000/api

## 📡 API Endpoints

### Express/MongoDB API

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/dealers` | Get all dealers |
| GET | `/api/dealers/:state` | Get dealers by state |
| GET | `/api/dealer/:id` | Get dealer by ID |
| GET | `/api/reviews/dealer/:id` | Get reviews for a dealer |
| POST | `/api/reviews` | Add a new review |

### Sentiment Analysis API

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/analyze` | Analyze sentiment of text |

## 🗂️ Project Structure

```
.
├── djangoapp/                 # Main Django application
│   ├── models.py             # Database models
│   ├── views.py              # View functions
│   ├── urls.py               # URL routing
│   ├── templates/            # HTML templates
│   └── static/               # CSS, JS, images
├── server/                   # Express microservice
│   ├── server.js             # Express app
│   ├── models/               # MongoDB schemas
│   └── package.json          # Node dependencies
├── sentiment_analyzer/       # Sentiment analysis service
│   └── sentiment_analyzer.py
├── .github/
│   └── workflows/
│       └── django.yml        # CI/CD configuration
├── manage.py                 # Django management script
├── requirements.txt          # Python dependencies
└── README.md                 # This file
```

## 🧪 Testing

Run Django tests:
```bash
python manage.py test
```

Run linting:
```bash
flake8 .
```

## 🚢 Deployment

### Deploy to IBM Cloud

```bash
# Login to IBM Cloud
ibmcloud login

# Target Cloud Foundry
ibmcloud target --cf

# Deploy application
ibmcloud cf push YOUR_APP_NAME
```

### Environment Variables

Create a `.env` file with the following variables:

```env
SECRET_KEY=your_django_secret_key
DEBUG=False
DATABASE_URL=your_database_url
MONGODB_URI=your_mongodb_uri
SENTIMENT_API_URL=your_sentiment_api_url
ALLOWED_HOSTS=your_domain.com
```

## 📸 Screenshots

### Home Page
![Home Page](screenshots/home.png)

### Dealer Reviews
![Dealer Reviews](screenshots/reviews.png)

### Add Review
![Add Review](screenshots/add_review.png)

### Admin Panel
![Admin Panel](screenshots/admin.png)

## 👥 Usage

1. **Register/Login**: Create an account or login with existing credentials
2. **Browse Dealers**: View all dealerships or filter by state
3. **View Reviews**: Click on a dealer to see customer reviews
4. **Add Review**: After logging in, submit your own review with car details
5. **Admin Access**: Login to `/admin` to manage car makes, models, and data

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 👨‍💻 Author

**Your Name**
- GitHub: https://github.com/jagrutisupe
- LinkedIn: https://www.linkedin.com/in/jagruti-supe/

## 🙏 Acknowledgments

- IBM Full Stack Developer Professional Certificate
- Course instructors and mentors
- Open source community

## 📞 Support

For issues and questions:
- Open an issue on GitHub
- Email: jagrutisupe@gmail.com

**Note**: This is a capstone project for educational purposes as part of the IBM Full Stack Developer Professional Certificate program.
