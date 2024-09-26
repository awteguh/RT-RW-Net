# Konfigurasi MIkrotik RB941-2nD untuk wifi vocheran / RT RW Net
Konfigurasi ini menggunakan Mikrotik RB941-2nD hAP yang include wlan di dalamnya yang bisa memancarkan wifi dan 4 port eternet, dimana masing masing port di setting :
* ether1 = ISP (digunakan untuk sumber Internet yang di ambil dari ISP)
* ether2 = PC (untuk menyeting mikrotik menggunakan PC)
* ether3&4 = Wlan (digunakan untuk hotspot yang nantinya bisa disalurken ke router sebagai Access Point)
* wlan1 = sebagai pemancar wifi
# konfigurasinya :

## Interface (Setting rename nama ether1, ether2 ether3 dan ether4 agar memudahkan konfigurasi nantinya)
![Screenshot 2024-09-25 150110](https://github.com/user-attachments/assets/7fc09998-3f0b-4966-84e4-a57fa2590d54)

enable wlan1 terlebih dahulu, dan pilih mode ap bridge
![Screenshot 2024-09-25 152804](https://github.com/user-attachments/assets/57434cef-0915-4b21-b91b-a02477c0e00a)

## Bridge (Kelompokan / group port ether3, ether 4 dan wlan1 yang nantikan akan menjadi hotspot login)
buat bridge terlebih dahulu dan sesuaikan nama yang akan di gunakan
![Screenshot 2024-09-25 150239](https://github.com/user-attachments/assets/c5523931-4a9d-4fe0-bab6-4a6e3ec7be14)

tambahkan anggota yang akan di bridge
![Screenshot 2024-09-25 150259](https://github.com/user-attachments/assets/b6406368-8489-46b0-bb73-7a5e7fb8c0be)

## DHCP Client (meminta IP address untuk port ether1-ISP mikrotik dari ISP agar bisa akses internet)
![Screenshot 2024-09-25 150548](https://github.com/user-attachments/assets/2c5abf27-88b3-4434-a88a-425505bd2735)

IP otomatis di berikan dari ISP ke ether1-ISP
![Screenshot 2024-09-25 150601](https://github.com/user-attachments/assets/9236ffb9-fb78-4cb9-ab17-d8647c2b1431)

## DNS Setting (agar ether1-ISP bisa mengakses internet)
tambahkan dns google 8.8.8.8 dan 8.8.4.4, centang allow remote
![Screenshot 2024-09-25 150702](https://github.com/user-attachments/assets/736cadb3-a511-4108-96f2-11820896a0e7)

untuk mengetest ether1-ISP sudah bisa akses internet atau belum bisa mengetest ping google.com pada terminal di winbox

## IP Address (menambahkan IP pada ether2-PC dan bridge-wlan)
tambahkan IP untuk ether2-PC 10.10.10.1/24 dan IP untuk bridge-wlan 11.11.11.1/24
![Screenshot 2024-09-26 130909](https://github.com/user-attachments/assets/e7292548-7605-42e2-bfbd-556c45716cc7)

## DHCP Server (menyebarkan IP / bagi-bagi IP yang di salurkan ke pengguna dari port ether2-PC dan bridge-wlan yang menyebarkan koneksi internet)
pilih ke DHCP Setup
![Screenshot 2024-09-25 151457](https://github.com/user-attachments/assets/0fdca7fd-1aed-48d4-8d31-b4957afe3674)

![Screenshot 2024-09-25 151653](https://github.com/user-attachments/assets/6d5e1708-ec55-4ba0-adad-0ab9d9406c6c)

## NAT
IP > Firewall > Nat
![Screenshot 2024-09-25 151755](https://github.com/user-attachments/assets/b4eeba9e-2de9-4e12-8974-e2db4fb20763)
![Screenshot 2024-09-25 151807](https://github.com/user-attachments/assets/7b366384-9dc6-41c7-90bf-99ce6fdc64bb)

## Hotspot (pilih hotspot interface bridge-wlan karena port ini yang akan di salurkan menjadi wifi vocheran/login pw)
![Screenshot 2024-09-25 152137](https://github.com/user-attachments/assets/296be521-cbe8-40ef-9e4d-7a8773c23d15)
* pada bagian `DNS Name` di isi sembarang, ini akan menjadi link login untuk memasukan user dan pw nantinya, contoh `mikrotikteguh.net`
* pada bagian user dan password di isi sesuai yang di inginkan yang nantinya di gunakan untuk login menggunakan wifinya.
* selanjutnya bisa dicoba untuk akses ke halaman login wifinya.

## SNTP Client (sync waktu agar bisa tracking kendalan mikrotik)
enable terlebih dahulu, untuk primary NTP Server bisa menggunakan `0.id.pool.ntp.org` dan secondary NTP Server `1.id.pool.ntp.org` atau lebih jelasnya mengakses `https://www.ntppool.org/zone/id` maka akan keluar angka-angkanya
![Screenshot 2024-09-25 152443](https://github.com/user-attachments/assets/ea309163-fa65-4706-83bd-ac18baa4e676)

# Mikhmon





