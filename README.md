# labspy08_ke12
NAMA    : Budi Ariyanto<p>
KELAS   : TI.21.A.1<p>
NIM     : 312110159<p>

Execute program main_data.py untuk menambahkan jumlah data dan berapa data yang akan diinput

![Tambah Data](https://github.com/ariandto/labspy08_ke12/blob/main/SC/sc1.png)


dan hasilnya akan seperti ini:

![Output](https://github.com/ariandto/labspy08_ke12/blob/main/SC/sc2.png)

Berikut Source code Mahasiswa.py untuk main trigger yang link ke main_data.py

Mahasiswa.py
```python
class Mahasiswa:

    def __init__(self, nama, n_absen, n_tugas, n_uts, n_uas):
        self.nama = nama
        self.n_absen = n_absen
        self.n_tugas = n_tugas
        self.n_uts = n_uts
        self.n_uas = n_uas
        self.percentageAbsen = 0
        self.percentageTugas = 0
        self.percentageUts = 0
        self.percentageUas = 0
        self.nilaiAkhir = 0
        self.averege = 0
        self.grade = ''

    def calculateNilai(self):
        self.percentageAbsen = (self.n_absen / 100) * 10
        self.percentageTugas = (self.n_tugas / 100) * 20
        self.percentageUts = (self.n_uts / 100) * 30
        self.percentageUas = (self.n_uas / 100) * 40
        
        self.nilaiAkhir = self.percentageAbsen + self.percentageTugas + self.percentageUts + self.percentageUas
        float(self.nilaiAkhir)

        print("Nilai Akhir: " + str(self.nilaiAkhir))

    def calculateAverege(self):
        self.averege = ((self.percentageAbsen + self.percentageTugas + self.percentageUts + self.percentageUas) + float(self.nilaiAkhir)) / 2
        float(self.averege)

        print("Nilai Rata-rata: " + str(self.averege))

    def generateGrade(self):
        if (float(self.averege) >= 80):
            self.grade = 'A'
        elif (float(self.averege) >= 70 and float(self.averege) < 80):
            self.grade = 'B'
        elif (float(self.averege) >= 60 and float(self.averege) < 70):
            self.grade = 'C'
        elif (float(self.averege) >= 50 and float(self.averege) < 60):
            self.grade = 'D'
        else: 
            self.grade = 'E'

        print("Grade: " + self.grade)
```

Berikut Source Code main_data.py yang menjadi interface atau eksekusi program
```python
# Define class mahasiswa
from Mahasiswa import Mahasiswa

def main():
    # Define empty array
    list = []

    # Set count from zero
    count = 0

    x = input("Masukan Jumlah Mahasiswa: ")
    print("\n")

    # while count less than x, e.g: 0 < 2
    # it will display input
    # after that, append object Mahasiswa into array list
    while (count < int(x)):
        count += 1
        print("================================")
        print("Mahasiswa ke: " + str(count))
        print("================================ \n\n")

        nama = input("Masukan Nama Mahasiswa: ")
        n_absen = input("Masukan Nilai Absen: ")
        n_tugas = input("Masukan Nilai Tugas: ")
        n_uts = input("Masukan Nilai UTS: ")
        n_uas = input("Masukan Nulai UAS: ")

        # Set value object to class Mahasiswa
        list.append(Mahasiswa(nama, int(n_absen), int(n_tugas), int(n_uts), int(n_uas)))
        print("\n")

    # mapping all data from list
    for obj in list:
        Mahasiswa.calculateNilai(obj)
        Mahasiswa.calculateAverege(obj)
        Mahasiswa.generateGrade(obj)

        print(obj.nama, obj.n_absen, obj.n_tugas, obj.n_uts, obj.n_uas, obj.nilaiAkhir, obj.averege, obj.grade, sep= ' ')
main()
```

