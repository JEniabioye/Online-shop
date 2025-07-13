#  MyShop – Django E-commerce Project

This is a fully functional e-commerce application built with **Django 5**.
It includes a product catalog, shopping cart, order system, email notifications via Celery, and task monitoring with Flower.

---

##  Features

- Product catalog with categories
- Product listing and detail views
- Shopping cart using Django sessions
- Update/remove cart items
- Checkout and order creation
- Email confirmation using Celery
- Monitor background tasks with Flower
- Admin dashboard for products, categories, and orders

---

##  Tech Stack

- Python 3.12
- Django 5.0.4
- Celery 5
- RabbitMQ
- Flower
- Pillow

---

##  Installation

### 1. Clone the repository

```bash
git clone https://github.com/JEniabioye/myshop.git
cd myshop
```

### 2. Create a virtual environment

```bash
python -m venv env
source env/bin/activate      # On Windows: .\env\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install Django==5.0.4 Pillow==10.3.0 celery flower
```

### 4. Apply database migrations

```bash
python manage.py migrate
```

### 5. Create a superuser

```bash
python manage.py createsuperuser
```

---

##  Usage

### Run the development server

```bash
python manage.py runserver
```

Visit: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

---

##  Celery + RabbitMQ Setup

### 1. Start RabbitMQ (using Docker)

```bash
docker run -d --hostname rabbit --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

### 2. Start Celery worker

```bash
celery -A myshop worker -l info
```

---

##  Monitor Tasks with Flower

```bash
celery -A myshop flower
```

Visit: [http://localhost:5555](http://localhost:5555)

Optional (with basic auth):

```bash
celery -A myshop flower --basic-auth=user:password
```

---

##  Email Configuration

Use Django's console backend during development:

```python
# settings.py
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
```

---

##  Admin Panel

Visit: [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

Use your superuser credentials to log in and manage:
- Products
- Categories
- Orders

---

##  Project Structure

```
myshop/
├── cart/
├── orders/
├── shop/
├── templates/
│   ├── cart/
│   ├── orders/
│   └── shop/
├── static/
└── manage.py
```

---

## 📝 License

MIT License
