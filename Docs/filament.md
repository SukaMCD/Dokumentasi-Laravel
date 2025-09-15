# 📘 Dokumentasi Filament

Kumpulan perintah Filament yang sering digunakan dalam pengembangan admin panel Laravel.

---

## 🔹 Command Filament

```bash
# ========== Instalasi ==========
# Install Filament di project Laravel
composer require filament/filament

# Publish konfigurasi & assets Filament
php artisan filament:install

# Menjalankan server development Laravel
php artisan serve


# ========== Admin User ==========
# Membuat user admin Filament
php artisan make:filament-user

# Hanya membuat user admin dengan peran tertentu
php artisan make:filament-user --role=admin


# ========== Resource ==========
# Membuat resource (Model + CRUD + Page)
php artisan make:filament-resource NamaModel

# Membuat resource khusus tanpa halaman index
php artisan make:filament-resource NamaModel --generate-only

# Membuat custom page untuk Filament
php artisan make:filament-page NamaPage

# Membuat widget untuk dashboard Filament
php artisan make:filament-widget NamaWidget


# ========== Utility ==========
# Clear cache Filament
php artisan filament:cache:clear

# Publish assets (misal setelah update)
php artisan vendor:publish --tag=filament-assets

# Menjalankan migration khusus Filament jika diperlukan
php artisan migrate
