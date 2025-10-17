# Projek_KDJK_Kel4_P2


# Aplikasi Web "Vendure"


## Sekilas Tentang

Vendure adalah headless e-commerce framework berbasis Node.js dan TypeScript, dibangun di atas NestJS. Vendure berfokus pada arsitektur modular dan fleksibel untuk pengembangan aplikasi e-commerce modern yang bisa diintegrasikan dengan berbagai frontend seperti React, Vue, atau Angular.


## Instalasi via Railway

## Prasyarat  
Sebelum memulai, pastikan Anda sudah memiliki:  
- Akun GitHub  
- Akun Railway  
- Repository untuk project vendure  

<br>

1. **Buat akun railway dengan akun GitHub dan login ke akun railway**  
<img width="1022" height="537" alt="Image" src="https://github.com/user-attachments/assets/6b491b2d-e817-4449-a011-d99cb5d7d299" />  
<br>  
<img width="1116" height="584" alt="image" src="https://github.com/user-attachments/assets/cb876054-3276-42ac-a0c6-e346e3a1f88f" />  

<br>

2. **Buat new project di railway**  
<img width="1118" height="583" alt="image" src="https://github.com/user-attachments/assets/53703781-fb9d-43be-8259-bb3ba622df24" />  

<br>

3. **Pilih template**  
<img width="1117" height="593" alt="image" src="https://github.com/user-attachments/assets/6ffe7929-4e4e-408a-8626-18c4899d3f21" />  

<br>

4. **Ketik "Vendure" pada bagian search, lalu pilih Vendure oleh Rasmus puls**  
<img width="1120" height="586" alt="image" src="https://github.com/user-attachments/assets/239ce578-e0ac-4059-a7f3-7daee8cbbff9" />  

<br>

5. **Konfigurasi railway web server**  
<img width="530" height="478" alt="image" src="https://github.com/user-attachments/assets/8785df04-4ddb-4daf-b8db-4143c4ecd1a9" />  
<br>  
<img width="536" height="511" alt="image" src="https://github.com/user-attachments/assets/f0a8a9d8-785b-406d-ba14-60fe667a5721" />  
<br>  
<img width="507" height="502" alt="image" src="https://github.com/user-attachments/assets/34e0289d-b323-4b9f-aec0-3590d123e123" />  
<br>  
<img width="530" height="500" alt="image" src="https://github.com/user-attachments/assets/fef0e3bc-afe2-43a7-9aae-b5a1c5b06aee" />  
<br>  
<img width="521" height="508" alt="image" src="https://github.com/user-attachments/assets/180225ad-d7e8-4e67-b554-7d8640869eee" />  
<br>  
<img width="519" height="511" alt="image" src="https://github.com/user-attachments/assets/6a7b32e2-dab7-4a13-9fa3-c520db6b1247" />  
<br>  
<img width="510" height="507" alt="image" src="https://github.com/user-attachments/assets/df28bed7-7f7d-4ab4-af92-4a229992465d" />  
<br>  
<img width="513" height="508" alt="image" src="https://github.com/user-attachments/assets/f00f94f3-270c-4113-b268-53c140a3f9f4" />  
<br>  
<img width="512" height="513" alt="image" src="https://github.com/user-attachments/assets/fbfe85f8-6580-4321-82d2-8e404cea01d6" />  

<br>

6. **Klik Deploy, tunggu hingga proses selesai**  
<img width="1201" height="628" alt="image" src="https://github.com/user-attachments/assets/bc44835e-f6dd-43d2-9138-7bd93bb2cb7b" />  
Railway akan menjalankan **docker-compose.yml** untuk vendure-backend  

```
docker-compose.yml
```
```
version: "3"
services:
  vendure-backend:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "${PORT}:${PORT}"
    command: ["npm", "run", "start:server"]
    volumes:
      - /usr/src/app
    environment:
      APP_ENV= "production"
      ASSET_VOLUME_PATH= ${{RAILWAY_VOLUME_MOUNT_PATH}}
      COOKIE_SECRET= "secret"
      DB_HOST= ${{Postgres.PGPRIVATEHOST}}
      DB_NAME= ${{Postgres.PGDATABASE}}
      DB_PASSWORD= ${{Postgres.PGPASSWORD}}
      DB_PORT= ${{Postgres.PGPRIVATEPORT}}
      DB_SCHEMA= "public"
      DB_USERNAME= ${{Postgres.PGUSER}}
      PUBLIC_DOMAIN= ${{RAILWAY_PUBLIC_DOMAIN}}
      STOREFRONT_URL= ${{vendure-storefront.RAILWAY_PUBLIC_DOMAIN}}
      SUPERADMIN_PASSWORD= "superadmin"
      SUPERADMIN_USERNAME= "superadmin"
      TEMPLATE_REPORTER_URL= "https://railway-template-reporter-production.up.railway.app"
```

```
Dockerfile
```
```
FROM node:20

WORKDIR /usr/src/app

COPY package.json ./
COPY package-lock.json ./
RUN npm install --production
RUN npm install -g concurrently

COPY . .

RUN npm run build

CMD ["sh", "-c", "npm run seed:once && npm run start"]
```


Sementara itu, Railway menjalankan railway pack untuk vendure-storefront
```
railpack
```
```
yarn install --frozen-lockfile
yarn run build
yarn run start
```

Database menggunakan Postgres yang di deploy dengan Docker
```
docker pull ghcr.io/railwayapp-templates/postgres-ssl:17.6
```
```
docker run ghcr.io/railwayapp-templates/postgres-ssl:17.6
```

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

3. Buat new project railway
```
railway init
```

4. Deploy dengan template vendure railway
```
railway deploy --template 6DeBLr
```

5. Cek environment backend, frontend, postgres
```
railway service
railway variables
```

6. Contoh modifikasi environment
```
railway variables --set "SUPERADMIN_PASSWORD=rahasia" --set "SUPERADMIN_USERNAME=akbar3776"
```


## Cara Pemakaian

1. **Buka link untuk admin**  
   https://vendure-backend-production-4c15.up.railway.app/admin/
<br>

2. **Login dengan username dan password**  
<br>

   <img width="1919" height="866" alt="LOGIN" src="https://github.com/user-attachments/assets/a0fa0afb-bced-4194-9c0d-5383d9c47622" />
<br><br>

3. **Sebelum mengupload product maupun collection admin akan ke homepage terlebih dahulu**  
<br>

   <img width="1919" height="870" alt="Screenshot 2025-10-17 193954" src="https://github.com/user-attachments/assets/ad4b28c7-9c5f-4a07-a6b3-2f54051f6a34" />
<br><br>

4. **Sebelum membuat product, jika ingin productnya menjadi zero tax maupun menggunakan tax khusus maka admin perlu menceklis dibagian settings -> tax rates**  
<br>

   Pada bagian ini selain admin bisa menggunakan settings tax yang sudah ada, admin juga bisa mencustom new tax rate sesuai kriteria barang dan regionalnya.  
<br>

   <img width="1919" height="864" alt="Group 9" src="https://github.com/user-attachments/assets/891d3e74-0adb-42c2-8a48-47d57bdd54d3" />
<br><br>

5. **Create Product**  
<br>

   Pada bagian kiri di homepage terlihat opsi **Products** yang dimana setelah diklik akan muncul halaman dengan tombol **New Product**.  
   Setelah mengklik **New Product**, admin bisa langsung mengisi **Product Name** juga dengan **Description**-nya.  
<br>

   <img width="1919" height="1735" alt="CREATE PRODUCT" src="https://github.com/user-attachments/assets/ad88b178-603a-45e3-af81-34859922756d" />
<br>

   Setelah **Product Name** dan juga **Description** terisi, admin bisa mengisikan **asset maupun gambar product**.  
   Untuk tahapannya:
   - Klik **Add asset**
   - Upload asset dan pilih gambar yang ingin diupload (bisa lebih dari 1)
   - Add asset untuk product  
<br>

   <img width="1919" height="2597" alt="ADD ASSET" src="https://github.com/user-attachments/assets/b68b9bd4-a4af-463c-ab37-eb63d850b53a" />
<br>

   Selanjutnya admin mengatur **Product Variants** dan juga **Harga**.  
   Untuk tahapannya:  
   - **Add options** → isi Option dan juga Option value (contoh tertera digambar)  
   - Macam variants akan langsung muncul dan admin bisa langsung mengisikan harga dan stock secara manual untuk setiap variant  
   - Setelah terisi semua, klik **Create**.  
   - Setelah muncul pop-up dengan kalimat **“Create New Product”**, maka admin berhasil menambahkan product baru untuk dijual.  
<br>

   <img width="3838" height="1742" alt="FILL OUT PRODUCT" src="https://github.com/user-attachments/assets/3d84e4a1-79fc-4c4c-aede-6929f8434667" />
<br><br>

6. **Create Collection**  
<br>

   Agar banyak product nanti terlihat lebih rapi dibuatlah collection untuk menggabungkan beberapa product dengan kategori yang sama.  
   Untuk tahapan membuat collection adalah:
   - Menuju page collection pada tab sebelah kiri dari homepage  
   - Create New Collection  
   - Mengisikan nama juga deskripsi dari collection tersebut  
   - Mengatur filter yang terdiri dari beberapa kategori:
     - By facet values
     - By product variant name
     - Manually select product variants
     - Manually select products  
   - Karena disini admin memilih *Manually select product* maka admin perlu memilih product terlebih dahulu  
   - Setelah lengkap semua klik **Create**  
   - Setelah muncul pop-up dengan kalimat **“Create New Collection”**, maka admin berhasil menambahkan Collection baru.  
<br>

   <img width="3838" height="2615" alt="CREATE COLLECTION" src="https://github.com/user-attachments/assets/f8f59609-8120-49c3-b6dd-186ab485fe90" />
<br><br>

7. **Update Product & Collection**  
<br>

   Jika admin menyadari ada kesalahan pengisian maka admin bisa memperbaikinya melalui update ini.  
   Untuk tahapannya sendiri sangat mudah, jika ingin mengupdate product maka ke bagian product, jika ingin mengupdate collection maka ke bagian collection.  
   Selanjutnya untuk tahap keduanya adalah:
   - Klik product/collection yang ingin diupdate melalui *Name* yang tertera  
   - Update product/collection  
   - Klik tombol **Update** di pojok kanan halaman  
   - Jika muncul pop up **"Updated Product / Updated Collection"**, maka proses update berhasil  
<br>

   <img width="3838" height="1743" alt="UPDATE" src="https://github.com/user-attachments/assets/5f276f65-a6b3-45fe-9faa-d38f03654cf6" />
<br><br>

8. **Pembatalan product maupun collection**  
<br>

   Untuk pembatalan hanya bisa mengubah visibilitas dari **Public** menjadi **Private**, untuk menyembunyikan product maupun collection yang ingin dihilangkan.  
   Untuk tahapannya adalah:
   - Buka bagian product maupun collection  
   - Klik product/collection yang ingin dihilangkan melalui *Name* yang tertera  
   - Ubah visibilitas  
   - Klik tombol **Update** di pojok kanan halaman  
   - Jika muncul pop up **"Updated Product / Updated Collection"**, maka proses penghapusan berhasil  
     

## Pembahasan

### Kelebihan
#### 1. Berbasis TypeScript & NestJS
Vendure dibangun sepenuhnya menggunakan TypeScript di atas framework NestJS yang kuat dan terstruktur. Hal ini membantu menjaga kualitas kode, meminimalkan bug, serta memudahkan kolaborasi antaranggota tim.
#### 2. Headless & Bebas Desain Frontend.
Dengan arsitektur headless, sistem backend Vendure terpisah sepenuhnya dari tampilan frontend. Kami dapat membangun antarmuka pengguna sesuai kebutuhan menggunakan React, Vue, atau framework lain tanpa batasan template bawaan.
#### 3. Sistem Plugin yang Fleksibel.
Vendure menyediakan sistem plugin modular yang memungkinkan kami menambahkan fitur khusus—seperti sistem poin, integrasi pembayaran, atau pengiriman—tanpa mengubah kode inti.
#### 4. Fitur yang Tersedia Siap untuk Komersial.
Secara bawaan, Vendure mendukung banyak channel, bahasa, mata uang, dan fitur lainnya. Sehingga kelebihan ini menjadikannya siap digunakan untuk kegiatan berskala menengah hingga enterprise.

### Kekurangan
#### 1. Ekosistem Masih Terbatas.
Jumlah plugin dan integrasi pihak ketiga belum sebanyak platform besar seperti Medusa atau Shopify, sehingga beberapa fitur perlu dikembangkan manual.
#### 2. Membutuhkan Pemahaman Teknis yang Kuat.
Karena berorientasi pada developer, penggunaan Vendure memerlukan pemahaman terhadap Node.js, TypeScript, dan GraphQL.
#### 3. Kesulitan Pengembangan bagi Pemula.
Struktur dan arsitektur Vendure cukup kompleks. Dibutuhkan waktu untuk memahami dan menyesuaikannya sebelum dapat melakukan kustomisasi lanjutan.

### Perbandingan dengan Medusa

| Aspek                         | **Vendure**         | **Medusa**                       | **Analisis Singkat**                                                   |
| :---------------------------- | :------------------ | :------------------------------- | :--------------------------------------------------------------------- |
| **Basis Pemrograman**         | TypeScript & NestJS | JavaScript & Express.js          | Vendure lebih aman secara tipe data, ideal untuk proyek kolaboratif.   |
| **Komunikasi Data (API)**     | GraphQL             | REST API                         | GraphQL lebih efisien dan fleksibel, REST lebih mudah dipahami pemula. |
| **Fitur untuk Komersial**     | Fitur bawaan        | Perlu konfigurasi tambahan       | Vendure unggul dalam manajemen multi-channel.                          |
| **Fleksibilitas Kustomisasi** | Plugin modular      | Modular hingga level core        | Medusa sedikit lebih bebas dalam modifikasi mendalam.                  |
| **Komunitas & Ekosistem**     | Aktif namun kecil   | Lebih besar dan berkembang cepat | Medusa unggul dalam jumlah plugin dan sumber belajar.                  |


## Referensi
- (https://docs.railway.com/guides/cli)
- (https://funkyton.com/vendure-tutorial/)
- (https://docs.vendure.io/guides/deployment/deploy-to-railway/)
