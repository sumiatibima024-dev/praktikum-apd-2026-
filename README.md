# praktikum-apd-2026-

```python
USER_BENAR = "sumi"        
PASS_BENAR = "105"         

kesempatan = 3
login_berhasil = False

for i in range(kesempatan):
    print(f"--- LOGIN (Percobaan ke-{i + 1}) ---")
    username_input = input("Masukkan Username: ")
    password_input = input("Masukkan Password: ")

    if username_input == USER_BENAR and password_input == PASS_BENAR:
        print("\nLogin Berhasil! Selamat datang di aplikasi rekap pengeluaran.")
        login_berhasil = True
        break
    else:
        sisa = kesempatan - (i + 1)
        if sisa > 0:
            print(f"Login Gagal. Sisa percobaan: {sisa}\n")
        else:
            print("Login Gagal. Sisa percobaan habis!")

if not login_berhasil:
    print("\n[ERROR] Akun terblokir karena salah login 3 kali. Program selesai.")
else:
    print("\n==========================================")
    uang_bulanan = int(input("Masukkan jumlah uang saku awal (Rp): "))
    total_pengeluaran = 0

    while True:
        sisa_uang = uang_bulanan - total_pengeluaran

        if sisa_uang <= 0:
            print("\n[PERINGATAN] Saldo kamu sudah habis! Program otomatis selesai.")
            break

        print("\n--- MENU UTAMA REKAP PENGELUARAN ---")
        print("[1] Catat Pengeluaran")
        print("[2] Cek Sisa Uang Saku")
        print("[3] Keluar")
        
        pilihan = input("Pilih menu (1-3): ")

        if pilihan == "1":
            while True:
                sisa_sekarang = uang_bulanan - total_pengeluaran

                if sisa_sekarang <= 0:
                    print("\nSaldo kamu sudah habis, tidak bisa mencatat pengeluaran lagi.")
                    break

                nominal = int(input("\nMasukkan nominal pengeluaran (Rp): "))

                if nominal > sisa_sekarang:
                    print(f"Gagal! Nominal melebihi sisa uang saku (Sisa: Rp{sisa_sekarang:,}).")
                else:
                    total_pengeluaran += nominal
                    sisa_sekarang = uang_bulanan - total_pengeluaran
                    print(f"Pengeluaran sebesar Rp{nominal:,} berhasil dicatat.")
                    print(f"Sisa uang saku kamu saat ini: Rp{sisa_sekarang:,}")

                tanya = input("\nApakah Anda ingin mencatat pengeluaran lagi? (Y/T): ").upper()
                if tanya != "Y":
                    print("Kembali ke Menu Utama...")
                    break

        elif pilihan == "2":
            sisa_sekarang = uang_bulanan - total_pengeluaran
            print("\n--- INFORMASI SISA UANG SAKU ---")
            print(f"Uang Saku Awal       : Rp{uang_bulanan:,}")
            print(f"Total Akumulasi      : Rp{total_pengeluaran:,}")
            print(f"Sisa Saldo Saat Ini  : Rp{sisa_sekarang:,}")

        elif pilihan == "3":
            print("\nTerima kasih telah menggunakan program rekapitulasi pengeluaran!")
            break

        else:
            print("Pilihan menu tidak valid. Silakan pilih 1, 2, atau 3.")
