# PostgreSQL Cheat Sheet

---

# Tipe Data PostgreSQL

| Tipe Data | Fungsi | Contoh | Kapan Digunakan |
|-----------|--------|---------|-----------------|
| `SERIAL` | Auto Increment | `1, 2, 3...` | Primary Key |
| `INT` | Bilangan bulat | `20` | Umur, stok, jumlah |
| `BIGINT` | Bilangan bulat besar | `9999999999` | Data dengan jumlah sangat besar |
| `DECIMAL(p,s)` | Bilangan desimal presisi | `1500000.50` | Harga, saldo |
| `VARCHAR(n)` | Teks dengan batas karakter | `"Akbar"` | Nama, email, kode |
| `TEXT` | Teks panjang | `"Lorem ipsum"` | Password hash, deskripsi |
| `BOOLEAN` | Nilai benar/salah | `TRUE` | Status aktif |
| `DATE` | Tanggal | `2026-07-31` | Tanggal lahir |
| `TIME` | Waktu | `08:30:00` | Jam operasional |
| `TIMESTAMP` | Tanggal & Waktu | `2026-07-31 08:30:00` | Login, transaksi |
| `JSONB` | Data JSON | `{"nama":"Akbar"}` | Data fleksibel |

---

# Constraint PostgreSQL

| Constraint | Fungsi | Contoh |
|------------|--------|---------|
| `PRIMARY KEY` | Identitas unik setiap data | `id SERIAL PRIMARY KEY` |
| `NOT NULL` | Kolom wajib diisi | `nama VARCHAR(100) NOT NULL` |
| `UNIQUE` | Nilai tidak boleh sama | `email VARCHAR(255) UNIQUE` |
| `DEFAULT` | Nilai bawaan | `attempt INT DEFAULT 0` |
| `FOREIGN KEY` | Menghubungkan tabel lain | `FOREIGN KEY (user_id) REFERENCES accounts(id)` |
| `CHECK` | Validasi nilai | `CHECK (price > 0)` |
| `REFERENCES` | Menentukan tabel yang dirujuk | `REFERENCES airports(id)` |

---

# Rekomendasi Tipe Data

| Data | Gunakan | Contoh |
|------|---------|---------|
| ID | `SERIAL PRIMARY KEY` | `id SERIAL PRIMARY KEY` |
| Nama | `VARCHAR(100)` | `Akbar` |
| Username | `VARCHAR(50)` | `akbar123` |
| Email | `VARCHAR(255)` | `akbar@gmail.com` |
| Password (Hash) | `TEXT` | `$2b$12$...` |
| Role | `VARCHAR(20)` | `ADMIN` |
| Umur | `INT` | `20` |
| Harga | `DECIMAL(12,2)` | `1500000.00` |
| Jumlah | `INT` | `3` |
| Status | `BOOLEAN` | `TRUE` |
| Deskripsi | `TEXT` | `Lorem ipsum` |
| Kode Bandara | `VARCHAR(3)` | `BPN` |
| Kode Penerbangan | `VARCHAR(10)` | `GA201` |
| Kota | `VARCHAR(100)` | `Balikpapan` |
| Tanggal | `DATE` | `2026-07-31` |
| Waktu | `TIME` | `08:30:00` |
| Timestamp | `TIMESTAMP` | `2026-07-31 08:30:00` |

---

# Fungsi SQL yang Sering Dipakai

| Fungsi | Kegunaan | Contoh |
|---------|----------|---------|
| `CURRENT_TIMESTAMP` | Waktu sekarang | `DEFAULT CURRENT_TIMESTAMP` |
| `NOW()` | Waktu sekarang | `SELECT NOW();` |
| `COUNT()` | Menghitung jumlah data | `COUNT(*)` |
| `SUM()` | Menjumlahkan data | `SUM(price)` |
| `AVG()` | Menghitung rata-rata | `AVG(price)` |
| `MIN()` | Nilai terkecil | `MIN(price)` |
| `MAX()` | Nilai terbesar | `MAX(price)` |

---

# Template Table

```sql
CREATE TABLE table_name (
    id SERIAL PRIMARY KEY,

    name VARCHAR(100) NOT NULL,

    description TEXT,

    price DECIMAL(12,2) DEFAULT 0,

    is_active BOOLEAN DEFAULT TRUE,

    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

# Template Foreign Key

```sql
CREATE TABLE flights (
    id SERIAL PRIMARY KEY,

    origin_airport_id INT NOT NULL,

    destination_airport_id INT NOT NULL,

    FOREIGN KEY (origin_airport_id)
        REFERENCES airports(id),

    FOREIGN KEY (destination_airport_id)
        REFERENCES airports(id)
);
```