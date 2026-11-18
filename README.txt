# Simulasi Modulasi dan Demodulasi AM Menggunakan GNU Radio

Proyek ini berisi *flowgraph* GNU Radio Companion (`.grc`) untuk menyimulasikan proses modulasi dan demodulasi sinyal **Amplitude Modulation (AM)** secara *real-time* maupun berbasis audio/simulasi.

## 📋 Prasyarat

* **GNU Radio:** Versi 3.8 atau 3.10+ (direkomendasikan)
* **Sistem Operasi:** Linux (Ubuntu/Debian), Windows, atau macOS
* **Perangkat Keras (Opsional):** SDR seperti RTL-SDR, HackRF, atau USRP (jika ingin menerima sinyal radio fisik, jika tidak cukup menggunakan simulasi bawaan)

## 🛠️ Blok Utama yang Digunakan

1. **Signal Source:** Menghasilkan sinyal informasi (pesan) dan sinyal pembawa (*carrier*).
2. **Multiply / Add Const:** Melakukan proses modulasi AM dengan rumus:
   $$s(t) = A_c [1 + m \cdot x(t)] \cos(2\pi f_c t)$$
3. **Throttle:** Membatasi penggunaan CPU saat berjalan dalam mode simulasi tanpa perangkat keras SDR.
4. **Channel Model (Opsional):** Menambahkan derau (*noise*) untuk menguji ketahanan sinyal.
5. **Low Pass Filter (LPF):** Menyaring frekuensi tinggi dan mengambil selubung sinyal (*envelope*).
6. **Complex to Mag / AM Demod:** Melakukan proses demodulasi untuk memulihkan sinyal informasi asli.
7. **QT GUI Time Sink & Frequency Sink:** Menampilkan bentuk gelombang domain waktu dan spektrum frekuensi.
8. **Audio Sink:** Mengeluarkan hasil demodulasi ke *speaker* (jika menggunakan sinyal audio).