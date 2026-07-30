# Analisa Dataset Penjualan Promosi UMKM Jabodetabek
Di tulisan ini aku akan bahas analisaku tentang **dataset penjualan promosi UMKM Jabodetabek**, raw data berupa .csv<br>
- Poin penting dari dataset:
1. Dataset milik satu UMKM di daerah Jakarta.
2. Dataset sudah bersih dari sumbernya, tidak ada missing value jadi tidak perlu data cleaning.
3. Data dari tanggal 1 Januari 2025 - 31 Desemeber 2025 (1 tahun).
4. Berisi 2.029 data transaksi, yang terdiri dari: 1.847 selesai, 100 dibatalkan, dan 82 refund.
5. Transaksi dilakukan melalui beberapa channel, yaitu: GoFood, GrabFood, POS Kasir (Offline), ShopeeFood, Tokopedia (Tiktok), dan website.
6. Berdasarkan bulan, transaksi terbanyak ada di Bulan Maret dan Desember sebesar 11%, dan paling sedikit ada di Bulan Januari sebesar 7%.
7. Berdasarkan hari, transaksi terbanyak ada di hari Sabtu dan Minggu sebesar 20%, dan paling sedikit ada di Hari Rabu dan Jumat sebesar 12%.  
8. Gross sales selama 1 tahun adalah Rp.101.687.000 dengan net sales sebesar Rp.85.566.450 (rata-rata perbulan 7.130.537).
<br>

```sql
-- BEBERAPA COMMAND SQL YANG AKU GUNAKAN:
-- Menghitung total net sales
SELECT SUM(net_sales)
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm;

-- Mengurutkan data berdasarkan tgl trx
SELECT * 
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm
ORDER BY transaction_date ASC;

-- Menampilkan transaksi selesai
SELECT * 
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm
WHERE order_status = 'Selesai';

-- Menampilkan transaksi berdasarkan hari
SELECT 
    day_name,
    COUNT(*) AS total_transaksi,
    ROUND(
        (COUNT(*)::DECIMAL / SUM(COUNT(*)) OVER()) * 100, 
        2
    ) AS persentase
FROM umkm_jabodetabek.dataset_penjualan_promosi_umkm
WHERE order_status = 'Selesai'
GROUP BY day_name
ORDER BY total_transaksi DESC;
```