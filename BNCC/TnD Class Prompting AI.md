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
	
	Contoh:
	Input:
	
	Classify the text into neutral, negative, or positive
	Text: I think the vacation is okay
	Sentiment:
	
	Output:
	Neutral
	
	Ketika menggunakan zero-shot prompting, kita harus fine-tune <u>instruction</u> kita
	Kalau zero-shot tidak berhasil/output kurang baik, kita bisa mulai kasih contoh -> Few-shot prompting
	
	Cons:
	- Less effective for specialized task
	- May produce inconsistent formatings
	- Bisa misinterpret request
	
	Good for:
	- Simple tasks
	- Pertanyaan informasi simple
	- Straightforward
	- Minimizing tokens

2. Few-shot prompting
	LLM sudah cukup canggih untuk menjawab instruksi zero shot, tapi untuk 
	task/pertanyaan yang sangat spesifik, kita harus beri demonstrasi/contoh.
	Model bisa "belajar" dalam konteks yang kita berikan.
	
	**Contoh:**
	Input:
	A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that uses the word whatpu is:
	We were traveling in Africa and we saw these very cute whatpus.
	 
	To do a "farduddle" means to jump up and down really fast. An example of a sentence that uses the word farduddle is:
	
	Output:
	When we won the game, we all started to farduddle in celebration.
	
	Modelnya bisa menjawab pertanyaan kita dengan hanya satu contoh untuk kata "whatpu" dan juga "farduddle"
	
	**Limitations**
	Few-shot prompting itu baik untuk task2 mayoritas, tapi tidak sempurna, apalagi task2 yang memerlukan reasoning.
	Model2 terbaru sudah terkategori sebagai reasoning model (Model akan menjawab task step by step)
	Tapi kita akan belajar cara prompting bernama 'Chain of thought prompting'.


3. Chain of thought prompting
	Walaupun model2 sekarang sudah termasuk reasoning model, belum tentu setiap task mereka akan selesaikan dengan "reasoning" (step by step) maka dari itu, kita harus secara eksplisit memberikan instruksi chain of thought
	
	Kita bisa gabung dengan few-shot untuk result yang lebih baik.
	
	Extreme example:
	The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
	A: Adding all the odd numbers (9, 15, 1) gives 25. The answer is False.
	
	The odd numbers in this group add up to an even number: 17,  10, 19, 4, 8, 12, 24.
	A: Adding all the odd numbers (17, 19) gives 36. The answer is True.
	
	The odd numbers in this group add up to an even number: 16,  11, 14, 4, 8, 13, 24.
	A: Adding all the odd numbers (11, 13) gives 24. The answer is True.
	
	The odd numbers in this group add up to an even number: 17,  9, 10, 12, 13, 4, 2.
	A: Adding all the odd numbers (17, 9, 13) gives 39. The answer is False.
	
	The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1. 
	A:
	
	Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.
	
	**Zero-shot COT prompting**
	Sesimpel menambahkan "Let's think step by step".
	Bagus kalau kita gak ada banyak contoh yang bisa kita kasih ke AI modelnya
	
	Benefit:
	- Seakan2 kita belajar step by step (Demonstrasi approach problem solving step by step)
	- Kalau hasilnya salah, bisa liat step mana yang error
	- Dengan mengajak AI untuk berpikir step by step, lebih likely jawabannya benar

4. Iterative prompting
	Kadang, untuk approach sebuah masalah/ pertanyaan yang kompleks, AI tidak bisa langsung menyelesaikan dengan satu prompt saja.
	Melainkan, kita harus secara iteratif memberi instruksi kepada AI secara iteratif.
	
	
5. Negative prompting
	Instructing the AI on what not to do.
6. Role prompting
	Giving AI a role


