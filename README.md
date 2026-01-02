# 📋 Job Application Web App

İş başvuru süreçlerini yönetmek için geliştirilmiş bir web uygulaması. Flask, MySQL ve Docker kullanılarak hazırlanmıştır.

## 🎯 Proje Hakkında

Bu proje, şirketlerin iş ilanlarını yayınlamasını ve adayların bu ilanlara başvurmasını sağlayan bir web uygulamasıdır. Admin paneli ve kullanıcı paneli olmak üzere iki farklı rol içermektedir.

## ✨ Özellikler

### 👤 Kullanıcı Özellikleri
- Kullanıcı kayıt ve giriş sistemi
- reCAPTCHA ile güvenli giriş
- Açık pozisyonları görüntüleme
- İş başvurusu yapma (CV yükleme ve ön yazı)
- Başvuru durumunu takip etme
- Gönderilen başvuruları inceleme

### 🔐 Admin Özellikleri
- Yeni iş pozisyonu oluşturma
- Pozisyonları yönetme (silme/pasife alma)
- Başvuruları görüntüleme ve değerlendirme
- Başvuruları onaylama veya reddetme
- CV dosyalarını indirme
- Tüm kullanıcıları listeleme

## 🛠️ Teknolojiler

| Teknoloji | Açıklama |
|-----------|----------|
| **Flask** | Python web framework |
| **MySQL 8.0** | Veritabanı |
| **Docker & Docker Compose** | Konteynerizasyon |
| **Flask-WTF** | Form yönetimi |
| **Flasgger** | Swagger API dokümantasyonu |
| **Werkzeug** | Şifre hashleme |
| **Google reCAPTCHA** | Bot koruması |

## 📁 Proje Yapısı

```
job-application-web-app/
├── docker-compose.yml          # Docker servisleri yapılandırması
├── flask_db.sql                # Veritabanı şeması ve örnek veriler
├── README.md
└── flask_app/
    ├── app.py                  # Ana uygulama dosyası
    ├── db.py                   # Veritabanı işlemleri
    ├── forms.py                # WTForms form tanımları
    ├── Dockerfile              # Flask container yapılandırması
    ├── requirements.txt        # Python bağımlılıkları
    ├── auth/                   # Kimlik doğrulama modülü
    │   ├── routes.py
    │   └── templates/
    │       ├── login.html
    │       └── register.html
    ├── admin/                  # Admin modülü
    │   ├── routes.py
    │   └── templates/
    │       ├── admin_panel.html
    │       ├── applications.html
    │       └── new_position.html
    └── user/                   # Kullanıcı modülü
        ├── routers.py
        └── templates/
            ├── user.html
            ├── new_application.html
            └── review_application.html
```

## 🗄️ Veritabanı Şeması

| Tablo | Açıklama |
|-------|----------|
| `users` | Kullanıcı bilgileri (ad, soyad, email, şifre hash, rol) |
| `positions` | İş pozisyonları (başlık, açıklama, departman, lokasyon, deadline) |
| `applications` | Başvurular (kullanıcı, pozisyon, döküman, ön yazı, durum) |
| `documents` | CV dosyaları (blob olarak saklanır) |
| `application_status` | Başvuru durumları (İnceleniyor, Onaylandı, Reddedildi) |

## 🚀 Kurulum

### Gereksinimler
- Docker
- Docker Compose

### 1. Docker Network Oluşturma

```bash
docker network create --subnet=172.18.0.0/16 mynet123
```

### 2. Projeyi Çalıştırma

```bash
# Proje dizinine gidin
cd job-application-web-app

# Containerleri başlatın
docker-compose up -d
```

### 3. Uygulamaya Erişim

- **Web Uygulaması:** http://localhost:5000
- **MySQL Veritabanı:** localhost:3306

## 📝 API Dokümantasyonu

Swagger UI üzerinden API dokümantasyonuna erişebilirsiniz:

```
http://localhost:5000/apidocs
```

## 🔧 Yapılandırma

### Docker Compose Servisleri

| Servis | Container Adı | Port | IP Adresi |
|--------|---------------|------|-----------|
| web | flask_app_compose | 5000 | 172.18.0.20 |
| db | mysql_compose | 3306 | 172.18.0.10 |

### Veritabanı Bilgileri

```
Host: 172.18.0.10
Database: flask_db
User: root
Password: 1234
```

## 📸 Ekran Görüntüleri

### Giriş Sayfası
- Kullanıcı adı ve şifre ile giriş
- reCAPTCHA doğrulaması

### Kullanıcı Paneli
- Açık pozisyonları listeleme
- Başvuru yapma
- Başvuru durumu takibi

### Admin Paneli
- Pozisyon yönetimi
- Başvuru değerlendirme
- Kullanıcı listeleme

## 🤝 Katkıda Bulunma

1. Bu repoyu fork edin
2. Feature branch oluşturun (`git checkout -b feature/yeniOzellik`)
3. Değişikliklerinizi commit edin (`git commit -m 'Yeni özellik eklendi'`)
4. Branch'inizi push edin (`git push origin feature/yeniOzellik`)
5. Pull Request açın

## 📄 Lisans

Bu proje öğrenme ve uygulama pratiği amacıyla hazırlanmıştır.

---

## 🌐 English

### About

This is a job application management web application built with Flask, MySQL, and Docker. It allows companies to post job positions and candidates to apply for them.

### Features
- User registration and authentication with reCAPTCHA
- Job position management (create, delete)
- Application submission with CV upload
- Application review and status tracking
- Admin panel for managing positions and applications

### Quick Start

```bash
# Create Docker network
docker network create --subnet=172.18.0.0/16 mynet123

# Start the application
docker-compose up -d

# Access at http://localhost:5000
```
