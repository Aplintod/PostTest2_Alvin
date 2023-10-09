from prettytable import PrettyTable

customer = []
data_iphone = []

def menu_admin():
    while True:
        print("-"*50)
        print("Menu Admin :\n")
        print("1. Tambah iPhone")
        print("2. Lihat iPhone")
        print("3. Update iPhone")
        print("4. Hapus iPhone")
        print("5. Kembali ke Menu")

        print("-"*50)
        pilihan_admin = input("Silahkan Pilih Opsi Menu : ")
        print("-"*50)

        if pilihan_admin == '1':
            tambah_iphone()
        elif pilihan_admin == '2':
            lihat_iphone()
        elif pilihan_admin == '3':
            update_iphone()
        elif pilihan_admin == '4':
            hapus_iphone()
        elif pilihan_admin == '5':
            break
        else:
            print("Pilihan Tidak Valid, Coba Lagi!")

def tambah_iphone():
    nama_produk = input("Masukkan Nama iPhone : ")
    harga_produk = input("Masukkan Harga iPhone : ")
    data_iphone.append({'iPhone' : nama_produk, 'Harga' : harga_produk})
    print("\niPhone Telah Ditambahkan!")

def lihat_iphone():
    table = PrettyTable()
    table.field_names = ["Kode", "iPhone", "Harga"]
    for i, ip in enumerate(data_iphone):
        table.add_row([i, ip['iPhone'], ip['Harga']])
    print(table)

def update_iphone():
    lihat_iphone()
    isi_tabel = int(input("Masukkan Kode Produk yang Ingin diupdate : "))
    if 0 <= isi_tabel < len(data_iphone):
        nama_produk = input("Masukkan Produk Baru : ")
        harga_produk = input("Masukkan Harga Produk Baru : ")
        data_iphone[isi_tabel] = {'iPhone' : nama_produk, 'Harga' : harga_produk}
        print("Produk Berhasil Diupdate!")
    else:
        print("Kode iPhone Tidak Valid!")

def hapus_iphone():
    lihat_iphone()
    isi_tabel = int(input("Masukkan Kode iPhone yang Ingin Dihapus : "))
    if 0 <= isi_tabel < len(data_iphone):
        del data_iphone[isi_tabel]
        print("Produk Berhasil Dihapus!")
    else:
        print("Kode Produk Tidak Valid!")

def menu_customer():
    while True:
        print("-"*50)
        print("Menu Customer :\n")
        print("1. Beli iPhone")
        print("2. Kembali ke Menu Login")

        pilihan_customer = input("\nSilahkan Pilih Opsi Menu : ")
        print("-"*50)

        if pilihan_customer == '1':
            beli_iphone()
        elif pilihan_customer == '2':
            break
        else:
            print("Pilihan Tidak Valid, Coba Lagi!\n")

def beli_iphone():
    while True:
        lihat_iphone()
        isi_tabel = int(input("\nMasukkan Kode iPhone yang Ingin Dibeli : "))
        if 0 <= isi_tabel < len(data_iphone):
            jumlah = int(input("Masukkan Jumlah Produk yang Ingin DIbeli : "))
            harga_total = int(data_iphone[isi_tabel]['Harga']) * jumlah
            print(f"Total Harga : {harga_total}")
            customer.append({'iPhone':data_iphone[isi_tabel]['iPhone'], 'Jumlah':jumlah, 'Harga Total':harga_total })
            print("Transaksi Berhasil")
            
            print("-"*50)
            lanjut = input("Apakah Anda Ingin Melakukan Transaksi Lain ? (Iya/Tidak) : ")
            print("-"*50)
            if lanjut == "Tidak":
                print("Transaksi Telah Berakhir!")
                print("Terimakasih Telah Berbelanja di Pipin Apple Store :D")
                break
        else:
            print("\nTransaksi Tidak Valid\n")


def utama():
    while True:
        print("Selamat Datang di Pipin Apple Store\n")
        print("1. Login Admin")
        print("2. Login Customer")
        print("3. Log Out")

        pilihan_login = input("\nSilahkan Pilih Opsi : ")

        if pilihan_login == "1":
            menu_admin()
        elif pilihan_login == "2":
            menu_customer()
        elif pilihan_login == "3":
            break
        else:
            print("\nPilihan Tidak Valid!")

if __name__ == "_main_":
    utama()

print("-"*50)
print("\t        Pipin Apple Store")
print("-"*50)
utama()
