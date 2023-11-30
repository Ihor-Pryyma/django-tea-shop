# MyShop - Django E-commerce Application
![Python Version](https://img.shields.io/badge/python-3.10+-blue.svg)
![Django Version](https://img.shields.io/badge/django-4.1.13-092E20.svg)
![Celery Version](https://img.shields.io/badge/celery-5.2.7-red.svg)
## Description
MyShop is a fully featured e-commerce web application built with Django 4. This application demonstrates advanced features and functionalities of Django, including product catalog, shopping cart, asynchronous task processing with Celery, payment processing using Stripe, and more.

## Features
- Product catalog with a variety of categories and products.
- User authentication and authorization.
- Shopping cart functionality.
- Order management system.
- Asynchronous task processing with Celery.
- Payment processing with Stripe.
- Integration with Redis for caching.

## Installation

### Prerequisites
- Python 3.9 or higher
- Redis server
- Stripe account for payment processing

### Steps
1. **Clone the Repository**
```bash
git clone git@github.com:Ihor-Pryyma/django-tea-shop.git
cd django-tea-shop
```
2. **Set up a Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate # On Unix or MacOS
venv\Scripts\activate # On Windows
```

3. **Install Dependencies**
```bash
pip install -r requirements.txt
```

4. **Redis Server**
- Ensure Redis server is up and running on your system.
- Default Redis configurations are assumed. Modify settings in `settings.py` if necessary.
```shell
docker run -it --rm --name redis -p 6379:6379 redis
```
5. **Stripe Configuration**
- Set up your Stripe keys in environment variables or in `settings.py`.
- https://dashboard.stripe.com/test/webhooks
```shell
brew install stripe/stripe-cli/stripe
stripe listen --forward-to localhost:8000/payment/webhook/
```
6. **Celery**
- Ensure you have a message broker like RabbitMQ or Redis running for Celery.
- Run Celery worker: `celery -A myshop worker -l info` and `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management`

7. **Migrate Database**
```shell
python manage.py migrate
```
8. **Run the Server**
```shell
python manage.py runserver
```
## Acknowledgments
- Antonio Melé for the insightful book "Django 4 By Example".