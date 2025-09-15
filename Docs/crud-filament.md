# 📘 Dokumentasi CRUD Filament

Membuat panel admin dan CRUD dengan Filament.

---

## 🔹 Command Filament

```bash
# ========== Instalasi ==========
# Install Filament di project Laravel
composer require filament/filament

# Publish konfigurasi & assets Filament
php artisan filament:install

# ========== Panel Admin ==========
# Hanya membuat user admin dengan peran tertentu
php artisan make:filament-user --role=admin

# ========== Buat Model ==========
# Membuat model
php artisan make:model NamaModel

# ========== Isi Model ==========
# Isi model
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Category extends Model
{
    use HasFactory;

    protected $primaryKey = 'id';
    protected $table = 'nama_table';

    protected $fillable = [
        'col1',
        'col2',
        'gambar',
    ];
}

# ========== Instalasi ==========
# Membuat resource (Model + CRUD + Page)
php artisan make:filament-resource NamaModel

# ========== Pengaturan form ==========
# Pengaturan Form dan Table berada di dalam:
app/Filament/Resources/Nama_crud_yang_dibuat/Schemas/Nama_crud_yang_dibuatForm.php # Form
app/Filament/Resources/Nama_crud_yang_dibuat/Tables/Nama_crud_yang_dibuatTables.php # Tables

# Jika ada col gambar di table database:
app/Filament/Resources/Nama_crud_yang_dibuat/Schemas/Nama_crud_yang_dibuatForm.php # Form
<?php

namespace App\Filament\Resources\Nama_crud_yang_dibuat\Schemas;

use Filament\Forms\Components\FileUpload;
use Filament\Forms\Components\TextInput;
use Filament\Schemas\Schema;

class ProductForm
{
    public static function configure(Schema $schema): Schema
    {
        return $schema
            ->components([
                TextInput::make('col1')
                    ->required(),
                TextInput::make('col2')
                    ->required(),
                FileUpload::make('gambar') # Gunakan FileUpload
                    ->image() 
                    ->directory('images') # Folder yang akan di taruh gambar
                    ->storeFileNamesIn('gambar_nama_file'),
            ]);
    }
}

# Setup table agar memunculkan gambar:
app/Filament/Resources/Nama_crud_yang_dibuat/Tables/Nama_crud_yang_dibuatTables.php # Tables
<?php

namespace App\Filament\Resources\Nama_crud_yang_dibuat\Tables;

use Filament\Actions\BulkActionGroup;
use Filament\Actions\DeleteBulkAction;
use Filament\Actions\EditAction;
use Filament\Tables\Columns\ImageColumn;
use Filament\Tables\Columns\TextColumn;
use Filament\Tables\Table;

class ProductsTable
{
    public static function configure(Table $table): Table
    {
        return $table
            ->columns([

                TextColumn::make('col1')
                    ->searchable(),
                TextColumn::make('col2')
                    ->searchable(),
                ImageColumn::make('gambar'),
            ])
            ->filters([
                //
            ])
            ->recordActions([
                EditAction::make(),
            ])
            ->toolbarActions([
                BulkActionGroup::make([
                    DeleteBulkAction::make(),
                ]),
            ]);
    }
}

# Buka halaman admin untuk mencoba CRUD
127.0.0.1:8000/admin