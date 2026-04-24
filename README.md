<div align="center">

# 🏢 EasyMeet

### Smart Meeting Room Reservation System

*Reliable scheduling · Real-time availability · Conflict-free bookings*

[![Django](https://img.shields.io/badge/Django-5.2+-092E20?style=flat&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)](https://www.sqlite.org/)
[![DRF](https://img.shields.io/badge/DRF-3.14+-red?style=flat&logo=django&logoColor=white)](https://www.django-rest-framework.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 📂 **This repository showcases the project through screenshots and documentation.**
> Source code is available upon request — feel free to reach out via [your email or LinkedIn].

</div>

---

## 📌 Overview

**EasyMeet** is a full-stack web application for managing meeting room reservations within an organization. It focuses on **reliability, real-time availability checking, and conflict-free scheduling**, giving users a streamlined booking experience while providing administrators with centralized control over all resources.

---

## ✨ Features

| Module | Description |
|--------|-------------|
| 🔐 **Authentication** | Registration, login, session management, password reset via email |
| 🏠 **Room Management** | Full CRUD — capacity, configuration, equipment assignment |
| 🔧 **Equipment Management** | Manage equipment by category and quantity |
| 📅 **Reservations** | Create, update, and cancel bookings with participant and equipment selection |
| ⚡ **Conflict Detection** | Backend overlap logic prevents double bookings in real time |
| 📆 **Planning Calendar** | Visual overview of all reservations |
| 🔍 **Advanced Search** | Filter reservations by room, date, status, and more |
| 📊 **Admin Dashboard** | Statistics and centralized resource management |
| 📧 **Notifications** | Email alerts for reservation status changes |

---

## 🛠️ Tech Stack

### Backend
- **Django 5.2+** — Python web framework
- **Django REST Framework 3.14+** — REST API layer
- **SQLite** — Database *(PostgreSQL or MySQL recommended for production)*

### Frontend
- **HTML5 / CSS3** — Django-rendered templates
- **Vanilla JavaScript** — UI interactivity
- **Inter** — Google Fonts typography

### Tooling
- **python-decouple** — Environment variable management
- **Pillow** — Image processing

---

## 👥 User Roles

| Role | Permissions |
|------|-------------|
| **User** | Book rooms and equipment · View personal history · Edit profile |
| **Admin** | Manage users, rooms, equipment · Approve/reject reservations · View statistics |

---

## ⚡ Conflict Detection

The core scheduling feature uses a time-overlap algorithm to guarantee no double bookings:

```python
def check_availability(self, start_time, end_time, exclude_reservation=None):
    overlapping = Reservation.objects.filter(
        room=self,
        start_time__lt=end_time,
        end_time__gt=start_time,
        status__in=['approved', 'pending']
    )
    if exclude_reservation and exclude_reservation.pk:
        overlapping = overlapping.exclude(pk=exclude_reservation.pk)
    return not overlapping.exists()
```

Two intervals `[A, B]` and `[C, D]` overlap if and only if `A < D` and `B > C`. The `exclude_reservation` parameter handles edit scenarios — a reservation won't conflict with itself when being updated.

---

## 📸 Screenshots

<p align="center"><img src="docs/screenshots/1.png" alt="Screenshot 1" width="700"/></p>
<p align="center"><img src="docs/screenshots/2.png" alt="Screenshot 2" width="700"/></p>
<p align="center"><img src="docs/screenshots/3.png" alt="Screenshot 3" width="700"/></p>
<p align="center"><img src="docs/screenshots/4.png" alt="Screenshot 4" width="700"/></p>
<p align="center"><img src="docs/screenshots/5.png" alt="Screenshot 5" width="700"/></p>
<p align="center"><img src="docs/screenshots/6.png" alt="Screenshot 6" width="700"/></p>
<p align="center"><img src="docs/screenshots/7.png" alt="Screenshot 7" width="700"/></p>
<p align="center"><img src="docs/screenshots/8.png" alt="Screenshot 8" width="700"/></p>
<p align="center"><img src="docs/screenshots/9.png" alt="Screenshot 9" width="700"/></p>
<p align="center"><img src="docs/screenshots/10.png" alt="Screenshot 10" width="700"/></p>
<p align="center"><img src="docs/screenshots/11.png" alt="Screenshot 11" width="700"/></p>
<p align="center"><img src="docs/screenshots/14.png" alt="Screenshot 14" width="700"/></p>
<p align="center"><img src="docs/screenshots/12.png" alt="Screenshot 12" width="700"/></p>
<p align="center"><img src="docs/screenshots/13.png" alt="Screenshot 13" width="700"/></p>
<p align="center"><img src="docs/screenshots/15.png" alt="Screenshot 15" width="700"/></p>
<p align="center"><img src="docs/screenshots/16.png" alt="Screenshot 16" width="700"/></p>
<p align="center"><img src="docs/screenshots/17.png" alt="Screenshot 17" width="700"/></p>
<p align="center"><img src="docs/screenshots/18.png" alt="Screenshot 18" width="700"/></p>
<p align="center"><img src="docs/screenshots/19.png" alt="Screenshot 19" width="700"/></p>
<p align="center"><img src="docs/screenshots/20.png" alt="Screenshot 20" width="700"/></p>
<p align="center"><img src="docs/screenshots/21.png" alt="Screenshot 21" width="700"/></p>

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

Built with ❤️ using Django · If this project helped you, consider giving it a ⭐