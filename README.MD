# Konfigurasi MIkrotik RB941-2nD untuk wifi vocheran / RT RW Net
Konfigurasi ini menggunakan Mikrotik RB941-2nD hAP yang include wlan di dalamnya yang bisa memancarkan wifi dan 4 port eternet, dimana masing masing port di setting :
* ether1 = ISP (digunakan untuk sumber Internet yang di ambil dari ISP)
* ether2 = PC (untuk menyeting mikrotik menggunakan PC)
* ether3&4 = Wlan (digunakan untuk hotspot yang nantinya bisa disalurken ke router sebagai Access Point)
* wlan1 = sebagai pemancar wifi
untuk konfigurasinya :

## Interface (Setting rename nama ether1, ether2 ether3 dan ether4 agar memudahkan konfigurasi nantinya)
![Screenshot 2024-09-25 150110](https://github.com/user-attachments/assets/7fc09998-3f0b-4966-84e4-a57fa2590d54)

## Bridge (Kelompokan / group port ether3, ether 4 dan wlan1 yang nantikan akan menjadi hotspot login)
buat bridge terlebih dahulu dan sesuaikan nama yang akan di gunakan
![Screenshot 2024-09-25 150239](https://github.com/user-attachments/assets/c5523931-4a9d-4fe0-bab6-4a6e3ec7be14)

tambahkan anggota yang akan di bridge
![Screenshot 2024-09-25 150259](https://github.com/user-attachments/assets/b6406368-8489-46b0-bb73-7a5e7fb8c0be)

## DHCP Client (meminta IP address untuk port ether1-ISP mikrotik dari ISP agar bisa akses internet)
![Screenshot 2024-09-25 150548](https://github.com/user-attachments/assets/2c5abf27-88b3-4434-a88a-425505bd2735)

IP otomatis di berikan dari ISP ke ether1-ISP
![Screenshot 2024-09-25 150601](https://github.com/user-attachments/assets/9236ffb9-fb78-4cb9-ab17-d8647c2b1431)

## DNS Setting (



