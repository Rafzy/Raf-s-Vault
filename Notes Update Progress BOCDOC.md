 Questions
1. Apakah Kolom Pengirim Dokumen Selain Risalah Rapat di Registrasi Dokumen perlu ditampilkan Seperti Kolom Kepada Risalah Rapat? Jika Tidak dibuat sperti Risalah Rapat, maka dibuat Apakah Jika Select Semua Dewan Komisaris, Keterangan di Kolom Pengirim menjadi "Dewan Komisaris" ???
	*Iya, namun dengan kondisi Selected Dekom sesuai dengan 
2. Jenis Nomor Dokumen apa saja yang akan ADA dan TIDAK ADA Routing Out?
	*Semua Jenis Nomor Dokumen pasti ada Routing Out, dan Routing Outnya itu sesuai dengan Dekom yang dipilih saat mengisi 'Kepada'
3. Untuk Menu List Penomoran, Otomatis Sort By Filter Tanggal, kemudian Nomor?
	*Iya*
4. Untuk registrasi dokumen detail, jika dokumen yang dipilih adalah risalah rapat, apakah pilihan "Yes, SK KOM" perlu di disable?
	*Iya, yes sk kom di disable untuk semua jenis dokumen selain new dokumen*

Progress overall:
1. Development 79%, overall 64%
2. Fitur yang ada progress: Create input form, saat registrasi dokumen
3. Progress di memo kom: Auto generate nomor, form memo kom, list memo kom, etc
4. Registrasi dokumen selain risalah rapat, dari dan kepada diganti checkbox
5. Registrasi dokumen list ditambahkan pagination & Searching

Notes:
1. Untuk tugas tanggung jawab, kepada dekom itu diganti menjadi "Dewan Komisaris" kalau semua dewan komisaris dipilih V
2. Kalau dewan komisari di master berubah, maka tulisan "dewan komisaris" juga sudah berubah V
3. Tambah penjagaan saat generate nomor dokumen, kalau input manual itu nomor available otomatis increment
4. Tambah penjagaan tanggal untuk semua input tanggal
5. Bisa edit kepada dan dari untuk jenis dokumen selain rispat
6. Dokumen yang bisa jadi sk kom itu **hanya** new document
7. Memo di new registrasi dokumen jadiin "Memo Komisaris"
8. New document di paling atas ketika new registrasi dokumen
9. Untuk sekarang langsung lompat ke new dokumen saja untuk progressnya
10. Tambah button cancel di registrasi dokumen untuk new dokumen, kalau cancel, flag di registrasi dokumen, dan SK KOM jadi inactive
11. Tanggal format yang benar!!
12. Rincian SK KOM dipisah page sendiri, dengan judul "Rincian SK KOM \[Bulan]"

> Poin untuk di Sampaikan
13. UAT adalah User Acceptance Test, yaitu user coba untuk menggunakan aplikasi. 
	di usahakan akan mulai minggu ini, kisaran Paling Lambat share link nya di hari Kamis
14. Prioritas utama UAT nya adalah mengecek fungsional dulu. Kerapian tampilan prioritas kedua. 
	Fungsional yang di cek dulu adalah alur utama aplikasi dengan case-case yang normal. Baru melakukan skenario unik yang kemungkinan dengan probabilitas yang paling mungkin dulu. Misal:
	a. Daftar Nomor Rispat Registrasi Dokumen, Preview PDF, Edit Tanggal Routing, Update Registrasi Dokumen, Cek Tugas Tanggung Jawab Dekom, Cek SK KOM. Periksa Output Excel/PDF TTJ Dekom dan SK KOM
	b. Daftar Nomor Dokumen selain Rispat, Registrasi Dokumen, dan seterusnya sama seperti Poin ADA
	c. Cek Skenario Unik dengan Probabilitas yang paling mungkin terjadi nya besar, baru ke skenario untuk dengan probabilitas terkecil
15. Mention dalam waktu yang tersisa kurang lebih 1 bulan ini komunikasi akan semakin intens, karena UAT terlihat sederhana alurnya tapi penjagaan alias detail2 kecilnya banyak
16. Beberapa page di set ke anonymous jadi tidak perlu login, ada beberapa page yang harus login. Jika harus login bisa pakai user dibawah ini: 
	List User BOCDOC
		Secretary
	Username : U066691 - Bcabcabca123
	 
		Staff
	Username : U064692 - Bcabcabca123
	Username : U052067 - Bcabcabca123
	 
		Reviewer
	Username : U062450 - bcabca123
	Username : U900175 - Bcabcabca123
17. Role masih belum di set, jadi login menggunakan user dan role apapun masih bisa akses semua halaman