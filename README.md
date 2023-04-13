# Tugas_Kedai_Kopi_OOP

1. Class Menu adalah class yang merepresentasikan sebuah menu pada Ananda Coffee. Class ini memiliki atribut private __nama dan __harga, dan getter method get_nama() dan get_harga().
2. Class AnandaCoffee adalah class yang merepresentasikan kafe Ananda Coffee. Class ini memiliki atribut private __menu, yaitu sebuah list yang berisi objek-objek dari class Menu.
3. Method tampilkan_menu() digunakan untuk menampilkan daftar menu yang tersedia pada Ananda Coffee.
4. Method pesan() adalah method utama yang akan dijalankan ketika program dijalankan. Method ini akan terus berjalan sampai pengguna memilih untuk tidak memesan lagi. Saat pertama kali dijalankan, method ini akan memanggil method tampilkan_menu().

class Menu:
    def __init__(self, nama, harga):
        self.__nama = nama
        self.__harga = harga
    
    def get_nama(self):
        return self.__nama
    
    def get_harga(self):
        return self.__harga

class AnandaCoffee:
    def __init__(self):
        self.__menu = [
            Menu("ES Kopi Susu", 11000),
            Menu("ES Kopi Coklat", 12000),
            Menu("ES Kopi Hitam", 11000),
            Menu("Ice Americano", 14000)
        ]

    def tampilkan_menu(self):
        print("""
        ==============================
        
        Ananda Coffe
        List Menu Minuman Kopi
     
        ==============================
        """)
        for i, menu in enumerate(self.__menu):
            print(f"{chr(65+i)}. {menu.get_nama()} : Rp {menu.get_harga()}")

    def pesan(self):
        while True:
            self.tampilkan_menu()
            pesan = input("masukkan list abjad menu kopi = ")
            if pesan.upper() not in [chr(65+i) for i in range(len(self.__menu))]:
                pilihan = input("menu tidak tersedia, silahkan masukkan abjad menu yang tersedia silahkan ulangi kembali Y/N =")
                if pilihan.upper() == "N":
                    print("Terima kasih atas kunjungan Anda!")
                    break
            else:
                menu = self.__menu[ord(pesan.upper()) - 65]
                jumlah_pesan = int(input("masukkan jumlah pesanan = "))
                harga = menu.get_harga() * jumlah_pesan
                ppn = int(harga * 0.1)
                diskon = 0
                if jumlah_pesan >= 5:
                    diskon = int(harga * 0.2)
                total_harga = harga - diskon + ppn

                print("--------------------------")
                print("Ananda Coffe")
                print("--------------------------")
                print("Menu :", menu.get_nama())
                print("Jumlah Pesan :", jumlah_pesan)
                print("Harga :", harga)
                print("Diskon :", diskon)
                print("PPN :", ppn)
                print("--------------------------")
                print("Jumlah Bayar :", total_harga)
                print("--------------------------")
                pilihan = input("apakah anda ingin order kembali Y/N =")
                if pilihan.upper() == "N":
                    print("Terima kasih atas kunjungan Anda!")
                    break


ananda_coffee = AnandaCoffee()
ananda_coffee.pesan()
