# **📦 How to Install Composer on Linux (Official & Updated Guide)**

This guide explains how to install **Composer**, the PHP dependency manager, on any Linux distribution using the latest recommended method.

Composer allows you to manage PHP packages and is required for modern frameworks such as **Laravel**, **Symfony**, **CodeIgniter 4**, and many others.

---

## **🧰 Prerequisites**

Make sure your system is updated and PHP CLI is installed.

```bash
sudo apt update
sudo apt install php8.3-cli
sudo apt install php8.3-xml
sudo apt install php8.3-mbstring
sudo apt install php8.3-sqlite3
sudo systemctl restart php8.3-fpm 2>/dev/null
```

Verify PHP:

```bash
php -v
```

You should see **PHP 8.3.x** (or higher).

---

## **⬇️ Step 1 — Download Composer Installer**

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

---

## **🔐 Step 2 — Verify Installer Signature (Recommended)**

Download the latest official signature:

```bash
php -r "copy('https://composer.github.io/installer.sig', 'composer.sig');"
```

Store expected signature:

```bash
EXPECTED_SIGNATURE="$(php -r 'echo trim(file_get_contents("composer.sig"));')"
```

Calculate actual signature:

```bash
ACTUAL_SIGNATURE="$(php -r 'echo hash_file("sha384", "composer-setup.php");')"
```

Compare:

```bash
if [ "$EXPECTED_SIGNATURE" = "$ACTUAL_SIGNATURE" ]; then
    echo "Installer verified"
else
    echo "Installer corrupt"
    rm composer-setup.php
fi
```

If verification shows **Installer verified**, proceed.

---

## **⚙️ Step 3 — Install Composer**

```bash
php composer-setup.php
```

This will generate:

```
composer.phar
```

---

## **🌍 Step 4 — Install Composer Globally**

Move Composer to a global directory so it can run from anywhere:

```bash
sudo mv composer.phar /usr/local/bin/composer
sudo chmod +x /usr/local/bin/composer
```

---

## **🔎 Step 5 — Test Installation**

```bash
composer --version
```

Expected output:

```
Composer version 2.x.x
```

---

## **🎉 Installation Complete**

Composer is now fully installed on your Linux machine and ready to use.

---

## **📚 Useful Commands**

| Purpose                    | Command                                           |
| -------------------------- | ------------------------------------------------- |
| Check version              | `composer -V`                                     |
| Create new Laravel project | `composer create-project laravel/laravel appname` |
| Update dependencies        | `composer update`                                 |
| Install dependencies       | `composer install`                                |

---

## **📄 License**

This guide is open-source and free to use in your GitHub repositories, documentation, or personal projects.

---
