# 📘 Dokumentasi Socialite

Kumpulan perintah dan panduan Socialite untuk login sosial di Laravel.

---

## 🔹 Command & Setup Socialite

```bash
# ========== Instalasi ==========
# Install Socialite via Composer
composer require laravel/socialite

# Tambahkan provider Socialite di config/app.php (Laravel < 5.5)
# 'providers' => [
#     Laravel\Socialite\SocialiteServiceProvider::class,
# ]

# Tambahkan facade (optional)
# 'aliases' => [
#     'Socialite' => Laravel\Socialite\Facades\Socialite::class,
# ]


# ========== Konfigurasi Provider ==========
# Tambahkan kredensial di .env
# Contoh Google:
# GOOGLE_CLIENT_ID=your-client-id
# GOOGLE_CLIENT_SECRET=your-client-secret
# GOOGLE_REDIRECT_URI=https://your-app.com/auth/google/callback


# ========== Route & Controller ==========
# Route untuk redirect ke provider
Route::get('auth/{provider}', [SocialiteController::class, 'redirect']);

# Route callback setelah login
Route::get('auth/{provider}/callback', [SocialiteController::class, 'callback']);

# Di Controller:
# public function redirect($provider) {
#     return Socialite::driver($provider)->redirect();
# }
#
# public function callback($provider) {
#     $user = Socialite::driver($provider)->user();
#     // login atau register user di sini
# }


# ========== Utility ==========
# Hapus cache config jika ada error
php artisan config:clear

# Test route dengan artisan serve
php artisan serve
