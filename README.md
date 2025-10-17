# Projek_KDJK_Kel4_P2


# Aplikasi Web "Vendure"


## Sekilas Tentang

Vendure adalah framework untuk sistem web aplikasi E-Commerce dengan pendekatan "headless framework" yang memisahkan antara frontend dengan backend.


## Instalasi via Railway

Prasyarat
Sebelum memulai, pastikan Anda sudah memiliki:
- Akun GitHub
- Akun Railway
- Repository untuk project vendure

  
1. Buat akun railway dengan akun GitHub
<img width="1022" height="537" alt="Image" src="https://github.com/user-attachments/assets/6b491b2d-e817-4449-a011-d99cb5d7d299" />
<img width="1116" height="584" alt="image" src="https://github.com/user-attachments/assets/cb876054-3276-42ac-a0c6-e346e3a1f88f" />



2. Login ke akun railway
3. Buat new project di railway
<img width="1118" height="583" alt="image" src="https://github.com/user-attachments/assets/53703781-fb9d-43be-8259-bb3ba622df24" />



4. Pilih template
<img width="1117" height="593" alt="image" src="https://github.com/user-attachments/assets/6ffe7929-4e4e-408a-8626-18c4899d3f21" />



5. Ketik "Vendure" pada bagian search, lalu pilih Vendure oleh Rasmus puls
<img width="1120" height="586" alt="image" src="https://github.com/user-attachments/assets/239ce578-e0ac-4059-a7f3-7daee8cbbff9" />



6. Konfigurasi railway web server
<img width="530" height="478" alt="image" src="https://github.com/user-attachments/assets/8785df04-4ddb-4daf-b8db-4143c4ecd1a9" />

<img width="536" height="511" alt="image" src="https://github.com/user-attachments/assets/f0a8a9d8-785b-406d-ba14-60fe667a5721" />

<img width="507" height="502" alt="image" src="https://github.com/user-attachments/assets/34e0289d-b323-4b9f-aec0-3590d123e123" />

<img width="530" height="500" alt="image" src="https://github.com/user-attachments/assets/fef0e3bc-afe2-43a7-9aae-b5a1c5b06aee" />

<img width="521" height="508" alt="image" src="https://github.com/user-attachments/assets/180225ad-d7e8-4e67-b554-7d8640869eee" />

<img width="519" height="511" alt="image" src="https://github.com/user-attachments/assets/6a7b32e2-dab7-4a13-9fa3-c520db6b1247" />

<img width="510" height="507" alt="image" src="https://github.com/user-attachments/assets/df28bed7-7f7d-4ab4-af92-4a229992465d" />

<img width="513" height="508" alt="image" src="https://github.com/user-attachments/assets/f00f94f3-270c-4113-b268-53c140a3f9f4" />

<img width="512" height="513" alt="image" src="https://github.com/user-attachments/assets/fbfe85f8-6580-4321-82d2-8e404cea01d6" />



7. Klik Deploy, tunggu hingga proses selesai
<img width="1201" height="628" alt="image" src="https://github.com/user-attachments/assets/bc44835e-f6dd-43d2-9138-7bd93bb2cb7b" />



8. Buat Repository baru pada GitHub
<img width="220" height="234" alt="image" src="https://github.com/user-attachments/assets/e0d464de-f2f3-47e1-b21c-93ce5072c41b" />

9. Isi Repository baru yang telah dibuat dengan Repository https://github.com/Akbar3776/Vendure.git
10. Klik vendure-backend dan pilih Settings
<img width="1211" height="627" alt="image" src="https://github.com/user-attachments/assets/e9817c2d-e2b5-4ca3-9771-d678e454779b" />



11. Klik Disconnect dan Connect Repo
<img width="1206" height="631" alt="image" src="https://github.com/user-attachments/assets/113b5e8b-805e-4db1-94bc-d7c0a9e07af1" />



12. Pada bagian Connect Repo, pilih Repository yang diisi Project Vendure
13. Lakukan hal yang sama pada vendure-storefront
14. Klik Deploy untuk Apply changes
<img width="1201" height="634" alt="image" src="https://github.com/user-attachments/assets/03b8cd07-262c-45cc-a714-4bd17aedeb0d" />



15. Tunggu hingga proses selesai
<img width="1200" height="627" alt="image" src="https://github.com/user-attachments/assets/06c369ea-8b95-4699-ab4c-2685b532a5b7" />

## Instalasi via Railway CLI
Instalasi Via Railway CLI

Kebutuhan Sistem:
Node.js 16 version

1. Buka terminal dan install railway
```
npm i -g @railway/cli
```

2. Login akun railway
```
railway login --browserless
```

3. Buat baru folder
```
mkdir <nama-project-baru>
```

4. Buat new project railway
```
railway init
```

5. Deploy dengan template vendure railway
```
railway deploy --template 6DeBLr
```

6. Cek environment backend, frontend, postgres
```
railway service
railway variables
```

7. Contoh modifikasi environment
```
railway variables --set "SUPERADMIN_PASSWORD=rahasia" --set "SUPERADMIN_USERNAME=akbar3776"
```

## Konfigurasi (opsional)

Setting server tambahan yang diperlukan untuk meningkatkan fungsi dan kinerja aplikasi, misalnya:
- batas upload file
- batas memori
- dll

Plugin untuk fungsi tambahan
- login dengan Google/Facebook
- editor Markdown
- dll


##  Maintenance (opsional)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi (opsional)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.


## Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
- Bandingkan dengan aplikasi web lain yang sejenis


## Referensi

Cantumkan tiap sumber informasi yang anda pakai.
