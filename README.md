# Chatbot AI Takanashi Hoshino

Proyek ini merupakan implementasi antarmuka chatbot berbasis HTML, CSS, dan JavaScript yang menampilkan karakter Takanashi Hoshino dari permainan Blue Archive. Sistem ini memanfaatkan Google Generative AI API (model Gemini untuk pemrosesan teks dan model Imagen untuk generasi gambar) guna mensimulasikan percakapan dan menghasilkan gambar sesuai dengan persona karakter Takanashi Hoshino.


## Fitur Utama

* **Representasi Persona Karakter:** Interaksi dengan pengguna dilakukan sesuai dengan persona Takanashi Hoshino, termasuk pola bicara, sifat, dan basis pengetahuan yang telah ditentukan.
* **Percakapan Berbasis Teks:** Memfasilitasi dialog berbasis teks antara pengguna dan AI. Respons AI dihasilkan berdasarkan persona karakter dan konteks percakapan.
* **Interaksi Gambar:** Pengguna dapat mengunggah gambar, dan sistem akan memberikan komentar terkait gambar tersebut.
* **Generasi Gambar oleh AI:** Memungkinkan pengguna untuk meminta AI ("Takanashi Hoshino") untuk menghasilkan gambar berdasarkan deskripsi teks.
* **Respons Streaming:** Teks dari AI ditampilkan secara bertahap (streaming) untuk meningkatkan dinamika interaksi.
* **Riwayat Percakapan:** Riwayat percakapan disimpan sementara dalam `sessionStorage` peramban pengguna.
* **Fitur Hapus Percakapan:** Menyediakan opsi untuk menghapus riwayat percakapan saat ini melalui modal konfirmasi.
* **Salin Pesan:** Memudahkan pengguna untuk menyalin respons teks dari AI ke clipboard.
* **Indikator Status:** Menampilkan indikator visual saat AI sedang memproses permintaan ("berpikir") atau menghasilkan gambar.
* **Pratinjau Gambar Unggahan:** Menampilkan pratinjau gambar yang akan dikirim oleh pengguna.
* **Desain Responsif:** Antarmuka pengguna dibangun menggunakan Tailwind CSS untuk adaptasi pada berbagai ukuran layar.
* **Penanganan Kesalahan Dasar:** Memberikan umpan balik dasar untuk isu terkait kunci API atau konektivitas jaringan.

## Teknologi yang Digunakan

* **HTML:** Struktur dasar antarmuka pengguna.
* **CSS (Tailwind CSS & Kustom):** Penataan visual dan gaya antarmuka.
* **JavaScript (Vanilla JS):** Logika inti aplikasi, manipulasi DOM, dan interaksi API.
* **Google Generative AI:**
    * **Model Gemini (spesifiknya `gemini-2.0-flash` dalam kode sumber):** Untuk generasi teks dan pemrosesan bahasa alami.
    * **Model Imagen (spesifiknya `imagen-3.0-generate-002` dalam kode sumber):** Untuk generasi gambar berbasis AI.
* **Fetch API:** Untuk melakukan permintaan asynchronous ke Google AI API.
* **SessionStorage:** Untuk penyimpanan sementara riwayat percakapan di sisi klien.

## Prasyarat

1.  **Peramban Web Modern:** Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, atau peramban modern lainnya.
2.  **Kunci API Google AI:**
    * Diperlukan kunci API dari Google AI Studio (atau Google Cloud dengan Generative Language API dan Vertex AI API untuk Imagen telah diaktifkan).
    * Kunci API dapat diperoleh melalui [Google AI Studio](https://aistudio.google.com/app/apikey).
    * Kunci ini akan digunakan untuk akses ke model teks (`gemini-2.0-flash`) dan model generasi gambar (`imagen-3.0-generate-002`). Pastikan kunci API Anda memiliki otorisasi yang sesuai.

## Pengaturan dan Konfigurasi

1.  **Unduh atau Klon Kode Sumber:**
    * Unduh berkas `index.html`.
    * Alternatifnya, klon repositori jika tersedia: `git clone https://github.com/TakanashiXenz/simple-chat-bot`

2.  **Konfigurasi Kunci API:**
    * Buka berkas `index.html` menggunakan editor teks.
    * Temukan baris kode JavaScript berikut:
        ```javascript
        const apikey_gemini = "AIzaSyB_6PFbktl04BHmkUOCODJxXm4ubKy3fww"; // <<< GANTI DENGAN KUNCI API ANDA
        ```
    * **Ganti string `"AIzaSyB_6PFbktl04BHmkUOCODJxXm4ubKy3fww"` dengan kunci API Google AI Anda yang valid.**

    **Catatan Keamanan:** Penyematan kunci API secara langsung dalam kode HTML/JavaScript sisi klien hanya disarankan untuk pengembangan lokal atau demonstrasi. **Jangan pernah memublikasikan kunci API Anda dalam repositori publik.** Untuk aplikasi produksi, implementasikan mekanisme pengelolaan kunci API yang aman (misalnya, melalui variabel lingkungan di sisi server).

3.  **Aktivasi API (Jika Diperlukan):**
    * Pastikan "Generative Language API" telah diaktifkan dalam Proyek Google Cloud yang terkait dengan kunci API Anda.
    * Akses ke model `imagen-3.0-generate-002` melalui endpoint `generativelanguage.googleapis.com` mungkin memerlukan konfigurasi proyek spesifik atau dapat berubah. Jika terjadi kendala, pertimbangkan penggunaan Vertex AI API untuk Imagen. Kode saat ini menggunakan endpoint langsung untuk kesederhanaan demonstrasi.

## Panduan Penggunaan

1.  **Buka Berkas HTML:** Buka berkas `index.html` (setelah konfigurasi kunci API) menggunakan peramban web.
2.  **Sapaan Awal:** Sistem akan menampilkan sapaan awal dari "Takanashi Hoshino".
3.  **Interaksi Teks:**
    * Ketikkan pesan pada kolom input di bagian bawah antarmuka.
    * Klik tombol kirim (ikon pesawat kertas) atau tekan tombol Enter.
4.  **Unggah Gambar:**
    * Klik ikon gambar di sebelah kolom input.
    * Pilih berkas gambar (maksimum 4MB). Pratinjau gambar akan ditampilkan.
    * Pesan teks dapat disertakan bersama gambar.
    * Klik tombol kirim. Sistem akan memberikan respons terkait gambar tersebut.
5.  **Permintaan Generasi Gambar:**
    * Ketikkan prompt deskriptif, misalnya, "Gambarkan pemandangan gunung di pagi hari."
    * Sistem akan mencoba menghasilkan gambar berdasarkan prompt tersebut. Proses ini mungkin memerlukan waktu.
6.  **Hapus Riwayat Percakapan:**
    * Klik ikon tempat sampah pada bagian header antarmuka.
    * Sebuah modal konfirmasi akan muncul. Klik "Iya, Hapus" untuk melanjutkan atau "Nggak Jadi" untuk membatalkan.
7.  **Salin Pesan AI:**
    * Arahkan kursor ke balon pesan AI. Ikon salin akan muncul.
    * Klik ikon tersebut untuk menyalin teks respons AI ke clipboard.

## Tutorial Penggunaan melalui Termux

Chatbot ini juga dapat diakses pada perangkat Android menggunakan Termux dengan langkah-langkah berikut:

1.  **Instalasi Termux:** Pastikan aplikasi Termux telah terpasang pada perangkat Android Anda.
2.  **Instalasi Python & Git (jika belum tersedia):**
    ```bash
    pkg update && pkg upgrade
    pkg install python git
    ```
3.  **Unduh Berkas Chatbot:**
    * Jika Anda mengunduh berkas `index.html` secara manual, pastikan berkas tersebut berada dalam direktori yang dapat diakses oleh Termux (misalnya, direktori `Download`).
        ```bash
        # Pindah ke direktori penyimpanan berkas, contoh:
        # cd /sdcard/Download
        ```
    * Jika dari repositori Git:
        ```bash
        git clone https://github.com/TakanashiXenz/simple-chat-bot
        cd simple-chat-bot
        ```
4.  **Edit Kunci API via Termux:**
    * Anda memerlukan editor teks dalam Termux, misalnya `nano`. Jika belum terinstal:
        ```bash
        pkg install nano
        ```
    * Buka berkas menggunakan `nano`:
        ```bash
        nano "index.html"
        ```
    * Cari baris `const apikey_gemini = "...";` (gunakan `Ctrl + W` dalam `nano` untuk pencarian).
    * Ganti dengan kunci API Anda yang valid.
    * Simpan perubahan (`Ctrl + X`, lalu `Y`, kemudian `Enter`).

5.  **Jalankan Server HTTP Sederhana:**
    * Antarmuka HTML ini memerlukan server web untuk dapat diakses. Python menyediakan modul server HTTP bawaan:
        ```bash
        python -m http.server 8080
        ```
        (Angka `8080` adalah nomor port. Anda dapat menggantinya jika diperlukan, misalnya `8000` atau `7000`).

6.  **Akses melalui Peramban di Android:**
    * Buka aplikasi peramban web pada perangkat Android Anda (misalnya, Chrome, Firefox).
    * Masukkan alamat berikut pada bilah alamat: `localhost:8080` (atau `127.0.0.1:8080`).
    * Jika Anda menggunakan port yang berbeda pada langkah sebelumnya, sesuaikan alamat ini (misalnya, `localhost:7000`).
    * Antarmuka chatbot akan ditampilkan.

7.  **Hentikan Server (Setelah Selesai):**
    * Kembali ke sesi Termux, tekan `Ctrl + C` untuk menghentikan server Python.

## Tinjauan Struktur Kode

* **HTML (`index.html`):** Mendefinisikan struktur utama antarmuka, termasuk header, area pesan, kolom input, modal, dan overlay pemuatan.
* **CSS (Blok `<style>` menggunakan Tailwind CSS dan gaya kustom):** Mengatur aspek visual dan penataan gaya antarmuka.
* **JavaScript (Blok `<script>`):**
    * **Konstanta:** `apikey_gemini`, `session_key`, `hoshinoInitialPrompt`, `imageGenerationKeywords`.
    * **Referensi Elemen DOM:** Variabel untuk interaksi dengan elemen HTML.
    * **`hoshinoInitialPrompt`:** String yang mendefinisikan persona AI, basis pengetahuan, dan instruksi respons. String ini dikirim ke Gemini API sebagai konteks awal.
    * **Variabel Status:** `selectedImageBase64`, `selectedImageFile`, `chatHistory`, `currentAIResponseElement`.
    * **Fungsi Inti:**
        * `initializeApp()`: Memuat riwayat percakapan atau memulai sesi baru dengan sapaan awal dari AI (respons streaming).
        * `sendMessage()`: Mengelola input pengguna (teks dan/atau gambar), memanggil Gemini API untuk respons teks (respons streaming).
        * `generateImageWithHoshino()`: Mengelola permintaan generasi gambar menggunakan Imagen API.
        * `displayUserMessage()`, `displayAIMessage()`: Fungsi untuk merender pesan pada antarmuka chat.
        * `saveChatHistory()`, `loadChatHistoryFromSession()`: Mengelola riwayat percakapan dalam `sessionStorage`.
        * `performClearChat()`: Menghapus data percakapan dari antarmuka dan penyimpanan.
        * Fungsi utilitas lainnya untuk pembaruan UI (pratinjau gambar, status tombol kirim, salin ke clipboard, notifikasi toast, modal, indikator pemuatan).
    * **Event Listeners:** Menangani interaksi pengguna (pengiriman pesan, input gambar, penghapusan riwayat, dll.).

## Kustomisasi Lanjutan

* **Modifikasi Persona AI:** Ubah konten string JavaScript `hoshinoInitialPrompt` untuk menyesuaikan kepribadian AI, basis pengetahuan, atau bahkan untuk menciptakan karakter chatbot yang berbeda.
* **Penyesuaian Tampilan:**
    * Modifikasi kelas Tailwind CSS secara langsung pada elemen HTML.
    * Ubah definisi gaya kustom dalam blok `<style>`.
* **Model API:**
    * Anda dapat bereksperimen dengan model Gemini yang berbeda (misalnya, `gemini-pro`) dengan mengubah URL API pada fungsi `initializeApp` dan `sendMessage`.
    * Demikian pula, jika model `imagen-3.0-generate-002` tidak lagi tersedia atau Anda ingin menggunakan model gambar lain, Anda perlu memperbarui `apiUrl` pada fungsi `generateImageWithHoshino` dan kemungkinan struktur payload permintaan.
* **Kata Kunci Generasi Gambar:** Modifikasi array `imageGenerationKeywords` untuk mengubah frasa pemicu fitur generasi gambar.

## Terima Kasih Kepada (TQTO)

* **MySelf**
* **My parents**
* **My God**
* **Gemini**
* **Yostar & Nexon Games**
* **My Friends**

---


Semoga dokumentasi ini memberikan panduan yang jelas dan bermanfaat.
