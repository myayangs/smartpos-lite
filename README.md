# SmartPOS Lite 🚀

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Laravel](https://img.shields.io/badge/laravel-v10-red)
![PHP](https://img.shields.io/badge/php-v8.2-blueviolet)
![Nginx](https://img.shields.io/badge/nginx-reverse--proxy-green)
![MySQL](https://img.shields.io/badge/mysql-8.x-orange)
![Deployment](https://img.shields.io/badge/deployment-CentOS%209%20VM-success)

SmartPOS Lite is a **Point of Sale (POS)** and **inventory management** system built with **Laravel 10** and **MySQL**, deployed on a **CentOS 9 Virtual Machine**. This project was prepared for a deployment-focused capstone with emphasis on **production deployment**, **CI/CD**, **monitoring**, and **security hardening**.

---

## ✨ Main Features

- Admin authentication and user/role management
- Product, category, customer, and supplier management
- POS transaction flow, cart, invoice, and order tracking
- Operational dashboard and database backup module

---

## 🛠️ Tech Stack

### Application Stack
- **Backend:** Laravel 10
- **Frontend:** Blade, Bootstrap, Tailwind CSS, Vanilla JavaScript
- **Database:** MySQL 8.x
- **Web Server:** Nginx
- **PHP Runtime:** PHP 8.2 + PHP-FPM


### DevOps Stack
- **Deployment Target:** CentOS 9 VM
- **CI/CD:** GitHub Actions
- **Metrics Monitoring:** Grafana, Prometheus, Node Exporter
- **Log Monitoring:** Loki, Grafana Alloy
- **Security:** firewalld, Nginx hardening, GitHub Secrets, environment-based configuration


## 🧱 System Architecture

User → Nginx → Laravel (PHP-FPM) → MySQL

Monitoring:
- Prometheus scrapes metrics from Node Exporter
- Grafana visualizes metrics
- Alloy collects Laravel and Nginx logs
- Loki stores logs
- Grafana visualizes logs

---

## 🚀 Local Development Setup

### 1. Clone the Repository
```bash
git clone https://github.com/myayangs/smartpos-lite.git
cd smartpos-lite
```

### 2. Install Dependencies
```bash
composer install
npm install
npm run build
```

### 3. Environment Setup
```bash
cp .env.example .env
php artisan key:generate
```

### 4. Database Setup & Seeding
```bash
php artisan migrate:fresh --seed
php artisan storage:link
```

### 5. Start Local Development Server
For local testing:
```bash
php -S 127.0.0.1:8080 -t public
```

If frontend assets need dev mode:
```bash
npm run dev
```

Access the app at:
```text
http://127.0.0.1:8080
```

---

## 🌐 Production Deployment

This application is deployed on a **CentOS 9 VM** using:
- Nginx
- PHP-FPM
- MySQL
- GitHub Actions (SSH-based deployment)

### Deployment Steps
1. Prepare the VM
2. Install server dependencies
3. Clone source code from GitHub
4. Install project dependencies
5. Configure `.env` production
6. Run migration and seeding
7. Configure Nginx and PHP-FPM
8. Run the application in production

---

## 🔄 CI/CD Pipeline

The CI/CD pipeline is implemented using **GitHub Actions**.

### Pipeline Flow
1. Checkout source code
2. Setup PHP and Node.js
3. Install Composer dependencies
4. Install Node dependencies
5. Build frontend assets
6. Run Laravel validation / test steps
7. Deploy to VM via SSH
8. Run migrations and recache Laravel config
9. Restart PHP-FPM and reload Nginx

### Workflow File
```text
.github/workflows/deploy.yml
```

### Deployment Trigger
- Automatic on push to `main`
- Manual trigger via `workflow_dispatch`

---

## 📊 Monitoring

Two monitoring dashboards are used in this project:

### 1. SmartPOS Lite - Infrastructure Monitoring
Displays:
- CPU usage
- Memory usage
- Disk usage
- Server uptime

Powered by:
- Grafana
- Prometheus
- Node Exporter

### 2. SmartPOS Lite - Logs Monitoring
Displays:
- Laravel application logs
- Nginx access logs
- Nginx error logs
- Request/error counters

Powered by:
- Grafana
- Loki
- Grafana Alloy

---

## 🔐 Security Measures

The project applies the following security practices:

- Sensitive values stored in `.env`
- Deployment secrets stored in **GitHub Actions Secrets**
- Production uses `APP_DEBUG=false`
- MySQL uses a **dedicated non-root database user**
- VM hardened using **firewalld**
- Nginx hardened and used as reverse proxy
- Public exposure limited to necessary ports only
- Monitoring services can be proxied through domain instead of exposing raw ports

---

## 📈 Scaling

Scaling is not implemented automatically in this project because deployment uses a single VM. However, **vertical scaling** can be applied by increasing server resources such as CPU, memory, and storage based on application needs.

---

## 🔑 Development Credentials

For development and testing purposes, the project may still use the default credentials provided by the base project:

| Role | Username | Password |
| --- | --- | --- |
| **Admin** | `admin` | `password` |

> In the production environment, these default credentials have been changed for security reasons and are no longer used.

---

## 🖼️ Submission Evidence

- Public application URL: `https://smartposlite.duckdns.org`
- Monitoring dashboard URL: `https://monitoring-smartposlite.duckdns.org`
---

## 📄 License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

---

## 👤 Author

Customized and deployed by **myayangs** for deployment and DevOps-focused capstone submission.
Base project adapted and extended for educational deployment purposes.
