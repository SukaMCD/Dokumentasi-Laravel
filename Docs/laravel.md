# 📘 Dokumentasi Laravel

Kumpulan perintah Laravel yang sering digunakan dalam pengembangan.

---

## 🔹 Command Laravel

```bash
# ========== Dasar ==========
# Membuat project Laravel baru
composer create-project laravel/laravel nama_project

# Menjalankan server development
php artisan serve


# ========== Database & Migration ==========
# Membuat file migration baru
php artisan make:migration create_nama_table

# Menjalankan semua migration
php artisan migrate

# Membatalkan migration terakhir
php artisan migrate:rollback

# Membuat seeder
php artisan make:seeder NamaSeeder

# Menjalankan seeder
php artisan db:seed --class=NamaSeeder


# ========== Model, Controller, dan Resource ==========
# Membuat model
php artisan make:model NamaModel

# Membuat controller
php artisan make:controller NamaController

# Membuat resource controller
php artisan make:controller NamaController --resource

# Membuat request validation
php artisan make:request NamaRequest


# ========== Auth & User ==========
# Membuat auth scaffolding (jika pakai Breeze)
php artisan breeze:install

# Membuat middleware
php artisan make:middleware NamaMiddleware


# ========== Utility ==========
# Clear cache
php artisan cache:clear

# Clear config cache
php artisan config:clear

# Membuat symbolic link untuk storage
php artisan storage:link

# Menampilkan daftar route
php artisan route:list
