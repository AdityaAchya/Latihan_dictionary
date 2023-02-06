# Latihan_dictionary
Repository ini dibuat untuk memenuhi tugas pertemuan 10 - Bahasa Pemrograman

Nama : Aditya Achya Ananta Nur

Nim : 312210714

Kelas : TI.22.C.9
# Latihan 1

1. Membuat folder baru "Praktikum5" serta membuat juga 2 file baru
<img width="218" alt="foto 0" src="https://user-images.githubusercontent.com/115473988/204161145-1b19292a-89c7-4bd5-9601-e5eccf1b4cde.png">

2. Buka file latihan1 dan masukan perintah sebagai berikut

```pyhton
# Buat Dictionary daftar kontak Nama sebagai key, dan nomor sebagai value
dict = {'Nama': ['Ari', 'Dina'],'Nomor Telepon':[6981267888,6987677776] }

# Tampilkan kontaknya Ari
print("Menampilkan Nomor Telepon Ari")
print(dict['Nomor Telepon'][0])
print('')

#Tambah kontak baru dengan nama Riko, nomor 087654544
print("Menambahkan data baru ")
dict['Nama'].append('Riko')
dict['Nomor Telepon'].append('087654544')
print(dict)

#Ubah kontak Dina dengan nomor baru 088999776
if 'Dina' in dict['Nama']:
    DinaIndex = dict['Nama'].index('Dina')
    dict['Nomor Telepon'][DinaIndex] = '088999776'
else:
    print("Merubah Nomor Telepon Dina")
    print(dict['Nomor Telepon'][1])
print("Merubah Nomer Telepon Dina")
print(dict)

#Tampilkan Semua Nama
print("Tampilkan Semua Nama ")
print(dict['Nama'])

# Tampilkan semua Nomor
print("Tampilkan Semua Nomor")
print(dict['Nomor Telepon'])

# Tampilkan daftar Nama dan nomornya
print("Tampilkan Daftar Nama Dan Nomor Telepon")
print(dict)

```
3. Berikut adalah hasilnya
![Praktikum5 1](https://user-images.githubusercontent.com/123864099/217010866-0d3aac3b-fb74-47b8-ac67-1419bfbb4bf9.PNG)


# Tugas Praktikum
1. Membuat flowchart program yang akan kita buat

![flowchart (2)](https://user-images.githubusercontent.com/115473988/204161471-ca567c33-538e-4162-a923-88638b144476.png)

2. Buka file "TugasPraktikum" dan masukan kode berikut yang sesuia dengan perintah flowchart diatas 

``` pyhton
from tabulate import tabulate

#Buat program sederhana yang akan menampilkan daftar nilai mahasiswa, dengan ketentuan sebagai berikut

# Program dibuat dengan menggunakan Dictionary
dictMahasiswa = {
    'No'    : [],
    'Nim'   : [],
    'Nama'  : [],
    'Tugas' : [],
    'Uts'   : [],
    'Uas'   : [],
    'Nilai Akhir' : [],
}
no = 0

# Tampilkan menu pilihan: (Tambah Data, Ubah Data, Hapus Data, Tampilkan Data, Cari Data)
def tambahData(no):

    nim    = int(input("Masukan Nim          : "))
    nama   = input("Masukan Nama             : ")
    tugas  = int(input("Masukan Nilai Tugas  : ")) 
    uts    = int(input("Masukan Nilai UTS    : "))
    uas    = int(input("Masukan Nilai UAS    : "))
    nilai_akhir = (tugas * 30 / 100 ) + (uts * 35 / 100 ) + (uas * 35 / 100)

    dictMahasiswa['No'].append(no)
    dictMahasiswa['Nim'].append(nim)
    dictMahasiswa['Nama'].append(nama)
    dictMahasiswa['Uts'].append(uts)
    dictMahasiswa['Tugas'].append(tugas)
    dictMahasiswa['Uas'].append(uas)
    dictMahasiswa['Nilai Akhir'].append(nilai_akhir)


def editData(nim):

    if nim in dictMahasiswa['Nim']:

        nimIndex = dictMahasiswa['Nim'].index(nim)
        print("Pilih data yang akan dirubah")

# Nilai Akhir diambil dari perhitungan 3 komponen nilai (tugas: 30%, uts: 35%, uas: 35%)
        while True:
            editApa = int(input(" (1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai Uts, \n (5) Nilai Uas, \n (0) Simpan perubahan & Keluar \n :"))
            if editApa == 1:
                newNim = int(input("Masukan Nim : "))
                dictMahasiswa['NIM'][nimIndex] = newNim
            elif editApa==2:
                newNama=input("Masukan Nama : ")
                dictMahasiswa['Nama'][nimIndex] = newNama
            elif editApa==3:
                newTugas = int(input("Masukan Nilai Tugas : "))
                nilai_akhir=(newTugas * 30 / 100) +(dictMahasiswa['Uts'][nimIndex] * 35 / 100 ) 
                + (dictMahasiswa['Uas'][nimIndex] * 35/100 )
                dictMahasiswa['Tugas'][nimIndex]= newTugas
                dictMahasiswa ['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa==4:
                newUts = int(input("Masukan Nilai Uts : "))
                nilai_akhir= (dictMahasiswa['Tugas'][nimIndex] * 30 / 100) + (newUts * 35/100) + (
                dictMahasiswa['Uas'][nimIndex] * 35 / 100)
                dictMahasiswa['Uts'][nimIndex] = newUts
                dictMahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa==5:
                newUas = int(input("Masukan Nilai Uas : "))
                nilai_akhir= (dictMahasiswa['Tugas'][nimIndex] * 30 / 100) + (dictMahasiswa['Uts'][nimIndex] * 35/100) + (
                newUas * 35 / 100)
                dictMahasiswa['Uas'][nimIndex] = newUas
                dictMahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 0:
                break
        else:
            print("Data tidak ditemukan")

def deleteData(nim):
    if nim in dictMahasiswa['Nim']:
        nimIndex = dictMahasiswa['Nim'].index(nim)

        del dictMahasiswa['No'][nimIndex]
        del dictMahasiswa['Nim'][nimIndex]
        del dictMahasiswa['Nama'][nimIndex]
        del dictMahasiswa['Tugas'][nimIndex]
        del dictMahasiswa['Uts'][nimIndex]
        del dictMahasiswa['Uas'][nimIndex]
        del dictMahasiswa['Nilai Akhir'][nimIndex]
        print("Data berhasil dihapus")
    else:
        print ("Data tidak ditemukan")

def cariData(nim):
    if nim in dictMahasiswa['Nim']:
        nimIndex = dictMahasiswa['Nim'].index(nim)

        hasilCari = {
            'No' : dictMahasiswa['No'][nimIndex],
            'Nim' : dictMahasiswa['Nim'][nimIndex],
            'Nama' : dictMahasiswa['Nama'][nimIndex],
            'Tugas' : dictMahasiswa['Tugas'][nimIndex],
            'Uts' : dictMahasiswa['Uts'][nimIndex],
            'Uas' : dictMahasiswa['Uas'][nimIndex],
            'Nilai Akhir' : dictMahasiswa['Nilai Akhir'][nimIndex],}

        print(hasilCari)
    else:
            print("Data tidak ditemukan")

# Tampilkan menu pilihan: (Tambah Data, Ubah Data, Hapus Data, Tampilkan Data, Cari Data)
while True :
    tanya = input( "(C) Menambah data, \n (R) Melihat semua data, \n (U) Update data, \n (D) Menghapus data, \n (F) Mencari data, \n (Q) Keluar Program : ")

    if tanya == "C":   
        while True:
            no += 1

            tambahData(no)
            tambahDataLagi = input("Tambah data lagi ? (y/n) :")
            if tambahDataLagi == 'n':
                break
    elif tanya == "R":
        print(tabulate(dictMahasiswa, headers= ['NO','NIM','NAMA','TUGAS','UTS','UAS','NILAI AKHIR'], tablefmt="fancy_grid"))
    elif tanya == "U":
        print(tabulate(dictMahasiswa, headers= ['NO','NIM','NAMA','TUGAS','UTS','UAS','NILAI AKHIR'], tablefmt="fancy_grid"))
        nim = int(input('Masukan nim untuk edit data :' ))
        editData(nim)
    elif tanya == "D":
        print(tabulate(dictMahasiswa, headers= ['NO','NIM','NAMA','TUGAS','UTS','UAS','NILAI AKHIR'], tablefmt="fancy_grid"))
        nim = int(input('Masukan nim yang mau dihapus :' ))
        deleteData(nim)
    elif tanya == "F":
        nim = int(input('Masukan Nim untuk mencari data: '))
        cariData(nim)
    elif tanya == "Q":
        break
 ````

3. Berikut adalah hasilnya

![Hasil Praktikum 5 1](https://user-images.githubusercontent.com/123864099/217015737-cd8c4c19-80b7-464d-98f2-94035bb4a5cb.PNG)

![Hasil Praktikum 5 2](https://user-images.githubusercontent.com/123864099/217015617-c50e9d14-f776-4477-9bc3-93a5b8d0bfae.PNG)

![Hasil Praktikum 5 3](https://user-images.githubusercontent.com/123864099/217015664-2cba80df-912d-409e-9490-648045a5dc67.PNG)



## TERIMA KASIH
### ADITYA ACHYA ANANTA NUR - 312210714 - TI.22.C. - TEKNIK INFORMATIKA - UNIVERSITAS PELITA BANGSA

