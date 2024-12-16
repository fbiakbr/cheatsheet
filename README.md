# cheatsheet

1. CREATE PROJECT
2. INSTALL LIVEWIRE
composer require livewire/livewire

3. SETTING ENV + MIGRATE
4. INSTALL FILAMENT
composer require filament/filament:"^3.2" -W
php artisan filament:install --panels
php artisan make:filament-user

5. CREATE MODEL
php artisan make:model Category -m
php artisan migrate
php artisan make:filament-resource Category --generate

php artisan storage:link (IF IMAGE)
APP_URL=http://127.0.0.1:8000 (IF USE STORAGE LINK)

$table->foreignId('categories_id')->constrained('category')->cascadeOnDelete(); (IF USE FOREIGN KEY) 

Forms\Components\Select::make('id_kelas')
                    ->relationship('category', 'categories_id')
                    ->required(),
(Change On TransactionResource)

6. Add this on Siswa Model
use Illuminate\Database\Eloquent\Relations\BelongsTo;
public function category(): BelongsTo
{
     return $this->belongsTo(Categories::class);
}
