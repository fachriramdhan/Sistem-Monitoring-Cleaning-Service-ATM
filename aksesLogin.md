# 🔐 AKSES LOGIN SISTEM

---

## 👥 DAFTAR AKUN LOGIN

### 1️⃣ **ADMIN**
```
Email    : admin@cleaning.com
Password : password
Role     : Administrator
```

**Akses:**
- ✅ Dashboard Admin
- ✅ Kelola CS (CRUD)
- ✅ Kelola Area (CRUD)
- ✅ Kelola ATM (CRUD)
- ✅ Kelola Inventory (CRUD + Tambah/Kurangi Stok)
- ✅ Monitoring Absensi
- ✅ Monitoring Laporan
- ✅ Print Laporan Harian
- ✅ Kelola Permintaan (Approve/Reject)

---

### 2️⃣ **KOORDINATOR**
```
Email    : koordinator@cleaning.com
Password : password
Role     : Koordinator
```

**Akses:**
- ✅ Dashboard Koordinator
- ✅ Monitoring Absensi (Read Only)
- ✅ Monitoring Laporan (Read Only)
- ❌ Tidak bisa CRUD Master Data
- ❌ Tidak bisa Print Laporan

---

### 3️⃣ **CLEANING SERVICE #1**
```
Email    : andi@cleaning.com
Password : password
Role     : CS
Nama     : Andi Wijaya
Area     : Jakarta Pusat, Jakarta Selatan
```

**Akses:**
- ✅ Dashboard CS
- ✅ Absensi (Create + View History)
- ✅ Laporan ATM (Create + View History)
- ✅ Permintaan Alat/Chemical (Create + View History)
- ❌ Tidak bisa akses data CS lain

---

### 4️⃣ **CLEANING SERVICE #2**
```
Email    : budi@cleaning.com
Password : password
Role     : CS
Nama     : Budi Santoso
Area     : Jakarta Utara
```

**Akses:**
- ✅ Dashboard CS
- ✅ Absensi
- ✅ Laporan ATM
- ✅ Permintaan Alat/Chemical

---

### 5️⃣ **CLEANING SERVICE #3**
```
Email    : citra@cleaning.com
Password : password
Role     : CS
Nama     : Citra Dewi
Area     : Jakarta Timur, Jakarta Barat
```

**Akses:**
- ✅ Dashboard CS
- ✅ Absensi
- ✅ Laporan ATM
- ✅ Permintaan Alat/Chemical

---

## 🔄 ALUR WORKFLOW TESTING

### **Scenario 1: CS Bekerja**
1. Login sebagai **CS** (`andi@cleaning.com`)
2. **Absen** terlebih dahulu
3. **Buat Laporan ATM** (hanya ATM di area yang dipilih saat absen)
4. **Ajukan Permintaan** alat/chemical jika perlu

### **Scenario 2: Admin Monitoring**
1. Login sebagai **Admin** (`admin@cleaning.com`)
2. **Lihat Monitoring Absensi** → Cek siapa yang sudah/belum absen
3. **Lihat Monitoring Laporan** → Cek laporan yang masuk
4. **Kelola Permintaan** → Approve/Reject permintaan dari CS
5. **Print Laporan Harian** → Download/Print laporan

### **Scenario 3: Koordinator Monitoring**
1. Login sebagai **Koordinator** (`koordinator@cleaning.com`)
2. **Monitoring Absensi** (Read Only)
3. **Monitoring Laporan** (Read Only)

---

## 🎯 QUICK TEST CHECKLIST

**Test sebagai CS:**
- [ ] Login berhasil
- [ ] Dashboard tampil
- [ ] Absensi berhasil (upload foto)
- [ ] Laporan ATM berhasil (upload 3 foto)
- [ ] Permintaan inventory berhasil
- [ ] Lihat riwayat absensi
- [ ] Lihat riwayat laporan

**Test sebagai Admin:**
- [ ] Login berhasil
- [ ] Dashboard tampil dengan stats lengkap
- [ ] CRUD CS berfungsi
- [ ] CRUD Area berfungsi
- [ ] CRUD ATM berfungsi
- [ ] CRUD Inventory berfungsi
- [ ] Monitoring absensi tampil
- [ ] Monitoring laporan tampil
- [ ] Approve permintaan berhasil (stok berkurang)
- [ ] Reject permintaan berhasil
- [ ] Print laporan harian berhasil

**Test sebagai Koordinator:**
- [ ] Login berhasil
- [ ] Dashboard tampil
- [ ] Monitoring absensi tampil
- [ ] Monitoring laporan tampil
- [ ] Tidak bisa akses menu admin

---

## 🔑 CARA LOGIN

1. Buka: `http://127.0.0.1:8000`
2. Akan redirect ke `/login`
3. Masukkan email & password
4. Klik "Log in"
5. Akan redirect ke dashboard sesuai role

---

## 🆘 JIKA LUPA PASSWORD

Jalankan seeder lagi untuk reset semua akun:

```bash
php artisan db:seed --class=UserSeeder
```

Atau reset manual di database:

```bash
php artisan tinker
```

Lalu:
```php
$user = User::where('email', 'admin@cleaning.com')->first();
$user->password = bcrypt('password');
$user->save();
```

---
