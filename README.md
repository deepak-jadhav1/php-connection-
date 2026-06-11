# 🎓 Vidyapeet — College Website with PHP & MySQL Contact Form

> **A fully responsive multi-section college website built with HTML, CSS, and JavaScript, featuring a live PHP + MySQL backend that captures and stores contact enquiries from the website's contact form.**

---

## 📌 Project Summary

| Detail | Info |
|---|---|
| **Type** | Full-Stack Web Application |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Backend** | PHP |
| **Database** | MySQL (via MySQLi) |
| **UI Libraries** | Swiper.js, Font Awesome 5, Google Fonts |
| **Responsive** | Yes — Mobile, Tablet, Desktop |
| **Purpose** | College landing page with database-connected contact form |

---

## 🎯 What This Project Does

**Vidyapeet** is a complete college/institute website with 7 fully-designed sections. The key technical feature is a **live PHP backend (`conne.php`)** that:

- Accepts `POST` form submissions (name, email, message)
- Connects to a **MySQL database** using `mysqli`
- Uses **prepared statements** (parameterised queries) to safely insert records into the `enquire` table
- Returns a success message on completion

This demonstrates a full frontend-to-database data pipeline — the contact form on the website writes directly to a MySQL table in real time.

---

## 🌐 Website Sections

| Section | Description |
|---|---|
| **Header** | Fixed navbar with smooth-scroll links, hamburger menu (mobile), and a slide-in login form |
| **Home** | Full-screen hero banner with a welcome message and CTA button |
| **About** | Institute overview with 25-year experience highlight and image layout |
| **Subjects** | Grid of BTech subjects — CSE, Civil, Design, Mechanical |
| **Courses** | 6-card course catalogue: Full Stack, AI, Software Dev, Data Science, Cloud Computing, Cyber Security |
| **Teachers** | Faculty cards with hover-reveal social media links |
| **Reviews** | Auto-playing Swiper.js testimonial carousel |
| **Blog** | 3-post blog card layout with image hover zoom |
| **Contact** | Form connected to PHP backend → MySQL database |
| **Footer** | Address, contact info (Bengaluru, Karnataka), and social links |

---

## 🏗️ Project Structure

```
php-connection-/
└── Frontend/
    ├── index.html       # Full website with all 7 sections
    ├── style.css        # Complete responsive stylesheet with CSS variables
    ├── script.js        # Navbar toggle, login form, Swiper.js carousel
    └── conne.php        # PHP backend — handles form POST → MySQL insert
```

---

## 🔥 Backend: PHP + MySQL (conne.php)

```php
<?php
    $name    = $_POST['name'];
    $email   = $_POST['email'];
    $message = $_POST['message'];

    $conn = new mysqli('localhost', 'root', '', 'contact');

    $stmt = $conn->prepare("INSERT INTO enquire(name, email, message) VALUES(?, ?, ?)");
    $stmt->bind_param("sss", $name, $email, $message);
    $stmt->execute();

    echo "Message Sent Successfully....";
?>
```

**What it does:**
- Connects to a local MySQL database named `contact`
- Uses **prepared statements** with `bind_param` — preventing SQL injection
- Inserts the enquiry into the `enquire` table
- Returns a confirmation message to the user

### MySQL Table Schema

```sql
CREATE DATABASE contact;

USE contact;

CREATE TABLE enquire (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    name    VARCHAR(100) NOT NULL,
    email   VARCHAR(100) NOT NULL,
    message TEXT         NOT NULL
);
```

---

## 🎨 Frontend Highlights

**CSS Architecture (`style.css`)**
- CSS custom properties (`--primary-color: #12c2b9`, `--secondary`, `--black`, `--white`) for consistent theming
- Smooth animated buttons with a fill-on-hover effect using `::before` pseudo-elements
- Shine sweep effect on course and blog card images
- Swiper.js integrated for the auto-playing testimonial carousel
- Fully responsive at 3 breakpoints: `991px`, `768px`, `450px`

**JavaScript (`script.js`)**
- Hamburger menu toggle for mobile navigation
- Slide-in login form panel (independent of navbar)
- Auto-closes nav/login on scroll
- Swiper carousel with autoplay, loop, and responsive `slidesPerView` breakpoints

---

## ⚙️ Setup & Installation

### Prerequisites
- A local server environment: **XAMPP**, **WAMP**, or **LAMP**
- PHP 7+
- MySQL

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/deepak-jadhav1/php-connection-.git
```

2. **Move files to your server root**
```bash
# For XAMPP on Windows:
cp -r php-connection-/Frontend /xampp/htdocs/vidyapeet

# For XAMPP on Linux/Mac:
cp -r php-connection-/Frontend /opt/lampp/htdocs/vidyapeet
```

3. **Create the MySQL database**
- Open **phpMyAdmin** → `http://localhost/phpmyadmin`
- Run the SQL schema above to create the `contact` database and `enquire` table

4. **Run the project**
- Start Apache and MySQL from the XAMPP Control Panel
- Visit `http://localhost/vidyapeet/index.html`

5. **Test the contact form**
- Fill in Name, Email, Message → click **Send Message**
- Check phpMyAdmin → `contact` → `enquire` to see the record inserted

---

## 🧰 Skills Demonstrated

| Category | Skills |
|---|---|
| **PHP Backend** | Form handling via `$_POST`, `mysqli` connection, prepared statements, `bind_param` |
| **Database** | MySQL CRUD, schema design, SQL injection prevention |
| **HTML5** | Semantic structure, multi-section single-page layout, form design |
| **CSS3** | CSS variables, Flexbox, CSS Grid, pseudo-elements, animations, media queries |
| **JavaScript** | DOM manipulation, event listeners, Swiper.js integration |
| **Responsive Design** | Mobile-first breakpoints, hamburger nav, fluid grid layouts |
| **Full-Stack Integration** | End-to-end flow: HTML form → PHP → MySQL |

---

## 👨‍💻 Author

**Deepak Dilip Jadhav**
Full-Stack Developer | PHP | MySQL | Frontend Web Development

---

> *This project demonstrates a complete client-server architecture — from a styled, responsive frontend to a PHP backend that persists user-submitted data in a relational database.*
