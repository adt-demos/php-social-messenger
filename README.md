# 💬 PHP Social Messenger

**PHP Social Messenger** is a **near real-time messaging** web app that lets users **chat with each other**, **manage their profile**, and **manage contacts** (search, block/unblock, clear history). It ships with a clean AJAX-driven UI, a lightweight **RESTful API** with **built-in interactive API docs**, and a simple **MySQL** schema — making it a solid reference project for learning classic PHP + jQuery/AJAX architecture.

<p align="left">
  <img src="https://img.shields.io/badge/PHP-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white" alt="PHP">
  <img src="https://img.shields.io/badge/MySQL-%234479A1.svg?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL">
  <img src="https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge" alt="License">
</p>

## 📚 Table of Contents

- [Features](#-features)
- [Demo Accounts](#-default-users-for-demo)
- [Project Structure](#-project-structure)
- [API Documentation](#-api-documentation)
- [Requirements](#-requirements)
- [Installation Guide](#️-installation-guide-)
- [Technologies Used](#-technologies-used)
- [License](#-license)
- [Contributing](#-contributing)
- [Connect with Me](#-connect-with-me)

## ✨ Features

### 1️⃣ Real-Time Messaging ⚡
✅ **Live updates:** The chat polls the server every second via AJAX, so new messages appear without a manual refresh.
✅ **Message status:** Shows the last sender and unread message count per contact.
✅ **Message actions:** Users can **edit, delete, or copy** their own messages.

![Real-Time Messaging](./src/images/real_time.png)

## 🔑 **Login Page**

![Login Page](./src/images/login.png)

### 🛠 **Default Users for Demo**

All seed accounts share the same password: `IQBOLSHOH`.

| 👤 Username  | 🔑 Password  | 📝 Description  |
|:-------------|:-------------|:-----------------|
| `iqbolshoh`  | `IQBOLSHOH`  | Developer / owner account |
| `client`     | `IQBOLSHOH`  | Test user 1       |
| `user_3`     | `IQBOLSHOH`  | Test user 2       |
| `user_4`     | `IQBOLSHOH`  | Test user 3       |
| `user_5`     | `IQBOLSHOH`  | Test user 4       |
| `user_6`     | `IQBOLSHOH`  | Test user 5       |
| `user_7`     | `IQBOLSHOH`  | Test user 6       |

### 2️⃣ Profile Management 👤
✅ **Edit profile:** Update your **profile picture, name, and password**.
✅ **View profile:** See details of the person you are chatting with.

![Profile Management](./src/images/profile-management.png)

### 3️⃣ Contact Search 🔍
✅ **Find contacts easily** using the **dynamic search bar**.
✅ **Manage contacts** & see unread messages on the homepage.

![Contact Search](./src/images/contact-search.png)

### 4️⃣ Block Users 🚫
✅ **Block people** from sending you messages.
✅ **Blocked notifications:** Users get alerts if they try to message someone who blocked them.
✅ **Easily accessible block menu** in the chat interface.

![Block Users](./src/images/block-users.png)

### 5️⃣ Chat Interface 💬
✅ **Full message history** when opening a chat.
✅ **Delete or copy** your own messages.
✅ **Live syncing** for a smooth messaging experience.

![Chat Interface](./src/images/chat-interface.png)

### 6️⃣ Menu Options 🎛️
✅ **View profile** of the person you're chatting with.
✅ **Clear chat** history with a specific user.
✅ **Block user** to prevent them from messaging you.

![Menu Options](./src/images/menu-options.png)

---

## 📂 Project Structure

```
php-social-messenger/
├── api/                    # RESTful backend endpoints (JSON responses)
│   ├── auth/               # login, signup, logout, session & availability checks
│   ├── doc.php             # Interactive, browsable API documentation
│   ├── send_message.php, fetch_messages.php, edit_message.php, delete_message.php
│   ├── fetch_contacts.php, fetch_profile.php
│   └── change_user_status.php, check_user_status.php, clear_messages.php
├── login/                  # Login page
├── signup/                 # Signup page
├── logout/                 # Logout handler
├── src/
│   ├── css/                # Stylesheets (chat, login/signup, profile modal)
│   ├── js/                 # jQuery + SweetAlert2
│   └── images/             # Screenshots & user profile pictures
├── chat.php                # Main chat interface (requires login)
├── index.php                # Homepage / contact list
├── config.php               # Database connection & query helper class
├── database.sql             # Schema + demo seed data
└── README.md
```

## 📖 API Documentation

Every endpoint is documented with purpose, method, required parameters, and example request/response — browse it live once the app is running:

```
http://localhost/php-social-messenger/api/doc.php
```

| # | Endpoint | Method | Purpose |
|---|----------|--------|---------|
| 1 | `api/auth/login.php` | POST | Authenticate a user and start a session |
| 2 | `api/auth/logout.php` | POST | End the current session |
| 3 | `api/auth/signup.php` | POST | Register a new account |
| 4 | `api/auth/check_availability.php` | POST | Check if a username/email is already taken |
| 5 | `api/auth/check_login.php` | SESSION | Verify whether the current session is logged in |
| 6 | `api/change_user_status.php` | POST | Block / unblock a user |
| 7 | `api/check_user_status.php` | POST | Check if you are blocked by another user |
| 8 | `api/clear_messages.php` | POST | Delete the conversation with a user |
| 9 | `api/delete_message.php` | POST | Delete a single message |
| 10 | `api/edit_message.php` | POST | Edit a previously sent message |
| 11 | `api/fetch_contacts.php` | GET | List contacts, with optional `?search=` filter |
| 12 | `api/fetch_messages.php` | POST | Fetch the full conversation with a contact |
| 13 | `api/fetch_profile.php` | POST | Fetch the logged-in user's profile |
| 14 | `api/send_message.php` | POST | Send a new message |

## 📋 Requirements

- PHP **7.4+** (with the `mysqli` extension enabled)
- MySQL / MariaDB
- Apache or Nginx (or PHP's built-in server for local testing)

## ⚙️ Installation Guide 🛠️

Follow these steps to set up **PHP Social Messenger** on your local server:

### 1️⃣ Clone the Repository 📥
```bash
git clone https://github.com/Iqbolshoh/php-social-messenger.git
```

### 2️⃣ Navigate to the Project Directory 📂
```bash
cd php-social-messenger
```

### 3️⃣ Set Up the Database 🗄️
`database.sql` already creates the database and seeds demo data, so just import it directly:
```bash
mysql -u yourusername -p < database.sql
```
> This creates the `social_messenger_db` database, its tables, and 7 demo users.

### 4️⃣ Configure Database Connection ⚡
- Open **`config.php`** and update your database credentials if they differ from the defaults:
  ```php
  define("DB_SERVER", "localhost");
  define("DB_USERNAME", "root");
  define("DB_PASSWORD", "");
  define("DB_NAME", "social_messenger_db");
  ```

### 5️⃣ Run the Application 🚀
- Deploy on a **PHP-compatible server** (e.g., Apache, Nginx), or use PHP's built-in server for quick testing:
  ```bash
  php -S localhost:8000
  ```
- Open your browser and go to:
  **`http://localhost/php-social-messenger`** (or `http://localhost:8000` if using the built-in server)

## 🖥 Technologies Used
![HTML](https://img.shields.io/badge/HTML-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-%23563D7C.svg?style=for-the-badge&logo=bootstrap&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-%23F7DF1C.svg?style=for-the-badge&logo=javascript&logoColor=black)
![jQuery](https://img.shields.io/badge/jQuery-%230e76a8.svg?style=for-the-badge&logo=jquery&logoColor=white)
![Font Awesome](https://img.shields.io/badge/Font%20Awesome-%23528DD7.svg?style=for-the-badge&logo=fontawesome&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-%234479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

## 📜 License
This project is open-source and available under the [MIT License](./LICENSE).

## 🤝 Contributing
🎯 Contributions are welcome! If you have suggestions or want to enhance the project, feel free to fork the repository and submit a pull request.

## 📬 Connect with Me
💬 I love meeting new people and discussing tech, business, and creative ideas. Let's connect! You can reach me on these platforms:

<div align="center">

[![Website](https://img.shields.io/badge/Website-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://iqbolshoh.uz)
[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:iilhomjonov777@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/iqbolshoh)
[![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/templates_uz_support)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/998776030033)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/iqbolshoh.dev)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@Iqbolshoh_dev)

</div>
