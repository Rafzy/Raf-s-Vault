# Introduction

## What is backend?
- Pengembangan fokus pada server side
- usually handle business logics, like handling database, user authentication, etc
- relies heavily on problem solving <- can determine performance of website

## Backend vs Frontend

**Backend** (Server side)
- Responsibilities:
	- Managing data
	- user authentication
	- business logics
	- communication between server and clients
- Languages:
	- Node.js
	- python
	- ruby
	- php
	- java
	- Etc

**Frontend** (Client side)
- Resposibilities:
	- Create interface
	- Organization
	- desing (Kindof)
	- PS: The responsibilities of frontend can be intertwined with UI/UX designers
- Languages:
	- HTML
	- CSS
	- Javascript


Despite these differences, Frontend and Backend must be able to work together to create a good, quick, responsive website that's appealing to the user


# Backend Frameworks

- **Node.js (with Express.js)**
	- Language: javascript
- **Django**
	- Language: Python
- **Ruby on Rails**
	- Language: Ruby
- **Laravel**
	- Language: PHP
	- Strengths:
		- A lot of built in features, easier for developers
	- Weaknesses:
		- Performance lag compared to other framework
- **Flask**
	- Language: Python
- **Spring Boot**
	- Language: Java
- **ASP.NET Core**
	- Language: C#

# Why Laravel?

1. Ease of Learning and Use
	1. Clear Syntax
	2. Comprehensive documentation
	3. Large community
2. Built in tools
	1. Authentication
	2. Routing
	3. Eloquent ORM
3. Blade templating engine
	1. Simple Templating
4. Laravel Artisan
	1. Built in CLI tools
	2. Automates repetitive tasks
5. And many more!


# How Laravel Works

## MVC

> Sebuah *practice* dimana dalam pengembangan suatu codebase, tanggung codebase tersebut dipisah menjadi 3 component dengan tanggung jawab masing2 yaitu Model, View, and Controller


- Model
	Komponen yang berinteraksi dengan database, seperti managing data, validasi data, dan mengrepresentasikan data (Biasanya menggunakan ORM)
- View
	Bagian presentation, ini komponen yang bertanggung jawab dalam tampilan yang diberikan kepada user, jadi biasanya bagian view ini berisi HTML, CSS, dan Javascript, view bisa menampung data yang telah diambil oleh Model
- Controller
	Sebagai intermediary antara Model dan juga View, tugasnya handle HTTP requests, meminta model query data, dan memilih view yang tepat sesuai request user


# Code practice

## Folder Structure

Directory app -> Menyimpan "Kode utama" buat codebase kita, didalamnya ada models dan controller (http)

Resources -> Isi tampilan view untuk users, jadi bagian komponen view kita itu ada di dalam folder resources

Routes -> Berisi routing/penjaluran, jadi ini bakalan handle requests dari user. Di bagian web itu tempat kita mendaftarkan web routes untuk aplikasi kita

public -> Tempat taro aset2 statis kita seperti gambar, video, music, dll

.env -> file untuk konfigurasi environment kita.


## Routing

- Kita ada satu route default ('/' -> Return view welcome)
- Kalau kita ganti URLnya, bakalan berubah apa yang perlu dikasih urlnya buat dapet view yang kita mau
- kita bisa return satu string aja seperti "Hello BNCC!"
- Kita bisa liat file view "welcome" yang di return oleh route defaultnya
- nah untuk filenya kita bisa notice kalau nama filneya adalah.blade.php, ini karena untuk file views, itu bakalan pake blade templating engine
- Untuk route ini kita bisa tambahin sebanyak2nya seperlunya kita

# View

- Nah dengan route yang kita udah bikin sebelumnya, kita bisa return satu file view
- View yang kita buat, itu dimasukkan ke dalam folder view, dengan filetype .blade.php
- nah gimana kalau kita mau gabung dengan css? kita bisa taro di folder public dengan nama "style.css", sama juga dengan javascript, tinggal kita hubungkan aja dengan \<link> untuk css, dan \<script> untuk javascript.


## Mengirim data dari route ke view

- Kita bisa kirim data ke view, dengan menambahkan sebuah array di dalam function view, pada file route kita
- Kita bisa kirim data dengan bentuk associative array, yang berisi dari key value pairs
- Key-nya akan menjadi variable, dan valuesnya bakalan menjadi value untuk setiap variablenya
- Untuk variablenya, kita bisa gunakan di file view dengan memanggil seperti variable biasa.