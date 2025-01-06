# Membuat Project UAS
# Data Diri
Nama : Rafli Dhiya Fadhaly

Nim : 312410251

Kelas : TI 24 A2
## Struktur Program
```python
# Program Showroom Mobil Sport dengan Konsep Modular dan OOP

# Class untuk data mobil
class CarData:
    def __init__(self, car_id, brand, model, price):
        self.car_id = car_id
        self.brand = brand
        self.model = model
        self.price = price

# Class untuk pengelolaan data mobil
class CarProcess:
    def __init__(self):
        self.cars = []

    def add_car(self, car_data):
        """Menambahkan data mobil baru"""
        self.cars.append(car_data)

    def validate_car_id(self, car_id):
        """Validasi apakah ID mobil unik"""
        for car in self.cars:
            if car.car_id == car_id:
                raise ValueError("ID Mobil sudah ada!")

    def display_cars(self):
        """Mengembalikan daftar mobil dalam bentuk tabel"""
        return [
            (car.car_id, car.brand, car.model, car.price) for car in self.cars
        ]

# Class untuk tampilan (view)
class CarView:
    @staticmethod
    def show_menu():
        print("\n=== Showroom Mobil Sport ===")
        print("1. Tambah Mobil")
        print("2. Tampilkan Daftar Mobil")
        print("3. Keluar")

    @staticmethod
    def input_car():
        try:
            car_id = input("Masukkan ID Mobil: ")
            brand = input("Masukkan Merk Mobil: ")
            model = input("Masukkan Model Mobil: ")
            price = float(input("Masukkan Harga Mobil: "))
            return CarData(car_id, brand, model, price)
        except ValueError:
            raise ValueError("Input tidak valid, pastikan harga berupa angka!")

    @staticmethod
    def display_cars(cars):
        print("\n=== Daftar Mobil ===")
        print(f"{'ID':<10}{'Merk':<15}{'Model':<15}{'Harga':<10}")
        print("-" * 50)
        for car in cars:
            print(f"{car[0]:<10}{car[1]:<15}{car[2]:<15}{car[3]:<10}")
        print("-" * 50)

# Fungsi utama program
class MainProgram:
    def __init__(self):
        self.car_process = CarProcess()
        self.car_view = CarView()

    def run(self):
        while True:
            self.car_view.show_menu()
            choice = input("Pilih menu: ")
            if choice == "1":
                try:
                    car_data = self.car_view.input_car()
                    self.car_process.validate_car_id(car_data.car_id)
                    self.car_process.add_car(car_data)
                    print("Mobil berhasil ditambahkan!")
                except ValueError as e:
                    print(f"Error: {e}")
            elif choice == "2":
                cars = self.car_process.display_cars()
                self.car_view.display_cars(cars)
            elif choice == "3":
                print("Keluar dari program. Terima kasih!")
                break
            else:
                print("Pilihan tidak valid, coba lagi.")

# Eksekusi program
if __name__ == "__main__":
    app = MainProgram()
    app.run()
```
## Program di atas adalah sistem showroom mobil sport sederhana menggunakan konsep modular dan OOP. Berikut adalah penjelasan setiap bagian kodenya:
### 1. Kelas CarData:
- Berfungsi untuk menyimpan data mobil (ID, merk, model, harga).
- Konstruktor __init__digunakan untuk menginisialisasi properti mobil.
### 2. Kelas CarProcess:
- Digunakan untuk memproses data mobil, seperti menambah ponsel baru ( add_car), memvalidasi ID mobil ( validate_car_id), dan menampilkan daftar mobil ( display_cars).
### 3. Kelas CarView:
- Bertugas sebagai antarmuka pengguna (view), termasuk menampilkan menu, menerima input data, dan mencetak tabel daftar mobil.
### 4. Kelas MainProgram:
- Berfungsi sebagai titik utama (utama) dari program.
- Mengatur alur menu, memproses input dari pengguna, dan menjalankan fitur-fitur program.
### 5. Fungsi Utama ( if __name__ == "__main__"):
- mengisyaratkan program langsung dijalankan, lalu memulai aplikasi showroom mobil.
