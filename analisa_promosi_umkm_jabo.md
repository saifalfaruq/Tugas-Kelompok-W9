# Analisa Dataset Penjualan Promosi UMKM Jabodetabek
Di tulisan ini aku akan bahas analisaku tentang **dataset penjualan promosi UMKM Jabodetabek**, raw data berupa .csv<br>
- Poin penting dari dataset:
1. Dataset sudah bersih dari sumbernya, tidak ada missing value jadi tidak perlu data cleaning.
2. Data dari tanggal 1 Januari 2025 - 31 Desemeber 2025 (1 tahun).
3. Berisi 2.029 data transaksi, yang terdiri dari: 1.847 selesai, 100 dibatalkan, dan 82 refund.
4. Transaksi dilakukan melalui beberapa channel, yaitu: GoFood, GrabFood,
<br>

```sql
-- BEBERAPA COMMAND SQL YANG AKU GUNAKAN:
-- Mengurutkan data berdasarkan tgl trx
SELECT * 
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm
ORDER BY transaction_date ASC;

-- Menampilkan transaksi selesai
SELECT * 
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm
WHERE order_status = 'Selesai';
```