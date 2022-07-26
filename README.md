###### Nama : Irdian Candra.w
###### Kelas: RPLl
###### No.Absen:28

# Modul 1

Soal Nomor1
Lakukan proses instalasi framework laravel kedalam folder sengan nama masing-masing

#### pertama kita akan merubah title nama


![image](https://user-images.githubusercontent.com/109930652/180921080-23df0c26-e5f9-4752-bd1e-41779b715a50.png)
```

#### langkah kedua.
kita akan memasukkan comand prompt cmd.

composer create.project laravel/laraver penjualan 
```
![image](https://user-images.githubusercontent.com/109930652/180920675-86b17b10-4f75-48e3-a55c-49ad40259184.png)

# Modul 2
### Soal 1 Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam modul ini.

#### Langkah Pertama.
pertama kita akan membuat folder model kategori, menggunakan perintah artisan pada terminal VS CODE sebagai berikut.
```
php artisan make:model kategori
```

#### Langkah Kedua.
lalu kita edit isi kategori sebagai berikut.

```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class barang extends Model
{
    use HasFactory;
    
    protected $table = 'barang';
}

```
![image](https://user-images.githubusercontent.com/109930564/180909170-cad5dcbd-4f01-4e39-9c3d-e7371cc605d0.png)

#### Langkah Ketiga
Selanjutnya kita akan membuat createKategoriTable, dan gunakan perintah artisan di terminal VS CODE dibawah ini.

```
php artisan make:migration create_Kategori_table
```

#### Langkah Keempat.
Selanjutnya isi createKategoriTable seperti di bawah ini.

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};

```
![image](https://user-images.githubusercontent.com/109930564/180911176-ac142d95-2c32-4abe-9e0d-c4c106314968.png)

#### Langkah Kelima.
Membuat KategoriTableSeeder, dengan menggunakan perintah artisan di terminal VS CODE dibawah ini.

```
php artisan make:seeder KategoriTableSeeder
```

#### Langkah Keenam.
Kemudian tambahkan use DB; agar bisa dijalankan, dan isi KategoriTableSeeder sebagai berikut.

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
        [
            'nama' => 'Perlengkapan Sekolah',
        ],
        [
            'nama' => 'Komputer',
        ],
        [
            'nama' => 'Sabun',
        ],
        [
            'nama' => 'Accesories',
        ],
        [
            'nama' => 'ATK',
        ]
        ));
    }
}

```
![image](https://user-images.githubusercontent.com/109930564/180912813-56b1aed4-2cc2-4636-a10a-7a1d9f2bc461.png)

#### Langkah Ketujuh.
Kita Akan Menambahkan codingan di modul DatabaseSeeder seperti dibawah ini.

```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(produkTableSeeder::class);
        $this->call(kategoriTableSeeder::class);
    }
}

```
![image](https://user-images.githubusercontent.com/109930564/180913386-b535308a-160a-48a8-aa38-d2acbfd6aca0.png)

### Soal 2
#### 2. Berikan data dengan menggunakan seeder yang telah anda pelajari pada modul ini.

Seeder digunakan untuk membuat contoh data pada database. Fitur ini sangat bermanfaat saat 
melakukan pengembangan suatu sistem yang dimana kita memerlukan suatu contoh data. Apalagi 
ketika membutuhkan contoh data yang banyak, fitur ini dapat membantu dari pada memasukan data 
satu persatu scara manual melalui PhpMyAdmin
