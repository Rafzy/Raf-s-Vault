#tnd

# Introduction

AI sudah berkembang secara pesat dalam 3-5 tahun belakangan ini.
Dulu saat ChatGPT baru saja keluar/baru mulai populer, masih sangat "barebones", hanya bisa menjawab pertanyaan2 dasar, matematika dasar pun masih bisa salah.
Sekarang:
- Model2 baru spt ChatGPT 4.1, Claude ai 3.7 Sonnet, model LLM terbesar zaman sekarang, sudah sangat powerful, bisa menjawab pertanyaan kompleks, dan memecahkan masalah spesifik
- Model tersebut juga ada free plan, dan juga model open source seperti deepseek membuat AI chatbots sangat accessible bagi siapapun

----
 
Tetapi, walaupun AI model sudah sangat canggih, kita juga harus bisa memanfaatkan chatbots tersebut dengan prompting yang benar.

Prompting yang baik = Jawaban/Hasil yang lebih baik dari chatbot tersebut.

Prompt -> Conversation starter untuk AI
Dari prompt pertama, kita bisa terus menambahkan prompt dengan chat selanjutnya, dan AI akan menjawab dengan konteks dari prompt2 sebelumnya juga

Prompt -> Frasa singkat, atau beberapa kalimat ataupun eberapa paragraf.
Bahkan model2 baru sudah bisa handle input multimodal (Gambar, Audio, etc).

Kita bisa anggap AI sebagai tool yang kita "program" dengan kata2 melainkan coding.

----

Masuk teori Sedikit saja

Sistem2 AI seperti Chatgpt, Claude, Deepseek, dll, adalah gabungan dari NLP dan Machine Learning.

NLP -> Salah satu bidang dalam AI, studi yang fokus memberikan komputer kemampuan untuk mengerti, menginterpretasi dan generasi bahasa manusia.

Machine Learning -> Bidang dalam AI juga, fokus dalam melatih komputer untuk menyelesaikan sebuah tugas, tanpa di program secara eksplisit

Garis bawah <u>NLP</u>, chatbot bisa memahami prompt kita seandainya kita berbicara dengan manusia lain, dan Machine Learning membuat model bisa terus belajar dari input kita dan user2 lain.

----

Membuat prompt efektif

Cara kita struktur prompt kita akan pengaruh output AI. ada term untuk mengstruktur prompt sebaik mungkin -> Prompt Engineering

Tiga strategi untuk prompt engineering yang baik (Give context, Be specific, Build on the conversation)

1. Give context 
	Beri konteks yang lebih spesifik untuk sebuah pertanyaan
2. Be specific
	Ketika memberi sebuah pertanyaan, haruslah spesifik
3. Build On the Conversation
	Model AI bisa mengingat konteks2 dari prompt sebelumnya, kembangkanlah prompt untuk output yang lebih baik


Teknik2 Prompting:
1. Zero-shot
	Memberikan instruksi/pertanyaan kepada LLM tanpa memberikan contoh.
	Karena LLM dilatih menggunakan data yang sangat besar, model2 ini bisa melakukan task/menjawab pertanyaan tanpa harus kita berikan contoh.
	Input:
	```
	Classify the text into neutral, negative, or positive
	Text: I think the vacation is okay
	Sentiment:
	```
	Output:
	`Neutral`
	

2. 