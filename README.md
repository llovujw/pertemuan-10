# Pertemuan ke 10

## Profil
| Variable | Isi |
| -------- | --- |
| **Nama** | Intan Virginia Aulia Putri |
| **NIM** | 312310657 |
| **Kelas** | TI.23.A.6 |
| **Mata Kuliah** | Bahasa Pemrograman |

### Latihan 1
- Buat Dictionary daftar kontak
- Nama sebagai key, dan nomor sebagai value
- Tampilkan kontaknya Ari
- Tambah kontak baru dengan nama Riko, nomor 087654544
- Ubah kontak Dina dengan nomor baru 088999776
- Tampilkan semua Nama
- Tampilkan semua Nomor
- Tampilkan daftar Nama dan nomornya
- Hapus kontak Dina
``` Python
list = {
    "Arii" : "081267888", "Dina" : "087677776"  
}
print("\nTampilkan kontak Arii :")
print(29*"=")
print(" {0:^2} |".format("Nama"), "Nomor Telepon")      
print("=============================")

# Tampilkan Kontak Ari
print(" {0:^2} |".format("Arii") ,list["Arii"],"\n")

# Tambah Kontak baru
list["Riko"] = "087654544"

# Ubah kontak dina dengan nomor baru
list["Dina"] = "088999776"

# Tampilkan semua Nama 
print("Tampilan semua Nama :")
print("=============================")
# Setelah di ubah
print(" {0:^2} |".format("Nama"), "Nomor Telepon")
print("=============================")

for x in list.keys():
    print(" {0:^2} |".format(x))
print("\n")

# Tampilkan Semua Nomor 
print("Tampilan semua Nomor :")
print("=============================")
# Setelah di ubah
print(" {0:^2} |".format("Nama"), "Nomor Telepon")
print("=============================")

for x in list.values():
    print(" {0:^2} |".format(x))
print("\n")


# Tampilkan daftar Nama & Nomor
print("Tampilan daftar Nama & Nomor :")
print("=============================")
# Setelah di ubah
print(" {0:^2} |".format("Nama"), "Nomor Telepon")
print("=============================")

for x, y in list.items():
    print(" {0:^2} |".format(x), (y))
print("\n")

# Menghapus Kontak Dina
print("Menghapus Kontak Dina :")
print(29*"=")
del list["Dina"]

print(" {0:^2} |".format("Nama"), "Nomor Telepon")
print("=============================")

for x, y in list.items():
    print(" {0:^2} |".format(x), (y))
print("\n")
```

#### Tampilan output
![gambar 1](screenshot/ss2.png)

### Tugas Praktikum
Buat program sederhana yang akan menampilkan daftar nilai mahasiswa, dengan ketentuan
- Program dibuat dengan menggunakan Dictionary
- Tampilkan menu pilihan: (Tambah Data, Ubah Data, Hapus Data, Tampilkan Data, Cari Data)
- Nilai Akhir diambil dari perhitungan 3 komponen nilai (tugas: 30%, uts: 35%, uas: 35%)
- Buat flowchart dan penjelasan programnya pada README.md
``` Python
list = {}

while True:
    c = input("\n(T)ambah, (U)bah, (H)apus, (C)ari, (L)ihat, (K)eluar: ")

    # Menambahkan data inputan 
    if c.lower() == 't':
        print("Tambah data :\n")
        nama    = input("Nama           : ")
        nim     = int(input("NIM            : "))
        uts     = int(input("Nilai UTS      : "))
        uas     = int(input("Nilai UAS      : "))
        tugas   = int(input("Nilai Tugas    : "))
        akhir = (tugas * 30/100) + (uts * 35/100) + (uas * 35/100)
        list[nama] = [nim, tugas, uts, uas, akhir]

    # Mengubah data inputan
    elif c.lower() == 'u':
        print("Ubah Data :")
        nama = input("\nMasukkan Nama  : ")
        if nama in list.keys():
            nim     = int(input("NIM            : "))
            uts     = int(input("Nilai UTS      : "))
            uas     = int(input("Nilai UAS      : "))
            tugas   = int(input("Nilai Tugas    : "))
            akhir = (tugas * 30/100) + (uts * 35/100) + (uas * 35/100)
            list[nama] = [nim, tugas, uts, uas, akhir]
        else:
            print("NAMA {0} TIDAK ADA!".format(nama))

    # Menghapus inputan Nama
    elif c.lower() == 'h':
        print("Hapus berdasarkan nama inputan :")
        nama = input("\nMasukkan Nama  : ")
        if nama in list.keys():
            del list[nama]
            print("\nData {0} berhasil di hapus".format(nama))
        else:
            print("NAMA {0} TIDAK ADA!".format(nama))
    
    # Mencari data yg sudah di input
    elif c.lower() == 'c':
        print("Cari data berdasarkan nama inputan :")
        nama = input("\nMasukkan Nama : ")
        if nama in list.keys():
            print("\nNama        : {0}".format(nama))
            print("NIM         : {0}".format(nim))
            print("Nilai UTS   : {0}".format(uts))
            print("Nilai UAS   : {0}".format(uas))
            print("Nilai Tugas : {0}".format(tugas))                  
            print("Nilai Akhir : {0}".format(akhir)) 
        else:
            print("NAMA {0} TIDAK ADA!".format(nama))
    
    # Menampilkan seluruh data 
    elif c.lower() == 'l':
        if list.items():
            print("-"*78)
            print("|                               Daftar Mahasiswa                             |")
            print("-"*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("="*78)
            i = 0
            for z in list.items():
                i += 1
                print("| {no:2d} | {0:15s} | {1:15d} | {2:5d} | {3:5d} | {4:7d} | {5:7.2f} |"
                      .format(z[0][:13], z[1][0], z[1][1], z[1][2], z[1][3], z[1][4], no=i))
            print("-"*78)
        else:
            print("-"*78)
            print("|                               Daftar Mahasiswa                             |")
            print("-"*78)
            print("|No. | Nama            |       NIM       |  UTS  |  UAS  |  Tugas  |  Akhir  |")
            print("-"*78)
            print("|                       TIDAK ADA DATA! Silakan tambah data                  |")
            print("-"*78)

    # Keluar program
    elif c. lower() == 'k':
        break

    else:
        print("\n INPUT {} TIDAK ADA!, Silakan pilih [T/U/H/C/L] untuk menjalankan program!".format(c))
```
`if c.lower()`: Kondisi ini memeriksa apakah string huruf kecil yang dihasilkan adalah benar. Dalam Python, string kosong dianggap salah, dan string yang tidak kosong dianggap benar.

#### Tampilan output
![gambar 1](screenshot/ss4.png)

## Flowchart
![gambar 1](screenshot/ss5.png)
