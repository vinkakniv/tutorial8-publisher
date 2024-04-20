# Advanced Programming - Tutorial


------------
## Overview

This repository contains the code and reflections for Tutorial 8 in Advanced Programming course by Vinka Alrezky As (NPM: 2206820200)❄️
- [Tutorial 8 - Subscriber](https://github.com/vinkakniv/tutorial8-subscriber)
- [Tutorial 8 - Publisher](https://github.com/vinkakniv/tutorial8-publisher)
------------
# Tutorial 8 - Publisher

### _Reflection_

> a. How many data your publsher program will send to the message broker in one
run?

Berdasarkan kode dalam program tersebut, program publisher akan mengirimkan lima data _messages_ ke _message broker_ dalam satu kali _run_. Method `publish_event` digunakan untuk mengirimkan pesan. Setiap panggilan fungsi tersebut menghasilkan pengiriman satu `UserCreatedEventMessage` ke _message broker_. Dalam `main` function, method `publish_event`
dipanggil sebanyak lima kali, yang berarti lima `UserCreatedEventMessage` akan dikirim selama satu sesi. Hal ini menunjukkan bahwa setiap kali program dijalankan, lima pesan akan secara konsisten dikirim ke _broker_. Ini merupakan bagian penting dari mekanisme publikasi dalam sistem berbasis _event-driven_, memungkinkan sistem untuk menangani dan menyebarkan event secara efisien.
> b. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber
program, what does it mean?

URL `amqp://guest:guest@localhost:5672` yang sama ditemukan di program subscriber menunjukkan bahwa kedua program, publisher dan subscriber, terhubung ke _message broker_ yang sama. Ini berarti bahwa pesan yang dikirim oleh publisher akan diterima oleh subscriber melalui _broker ini_. `localhost:5672` menunjukkan bahwa _broker_ beroperasi di mesin lokal dengan port 5672, yang merupakan konfigurasi standar untuk koneksi AMQP. Penggunaan _username_ dan _password_ yang sama (guest) dalam kedua URL juga menunjukkan bahwa akses ke _broker_ diatur dengan kredensial yang identik. Hal ini memudahkan manajemen keamanan, seringkali digunakan dalam pengembangan dan pengujian. Koneksi ini mendukung lingkungan pengembangan yang terisolasi dan aman, di mana interaksi antara publisher dan subscriber dapat diuji dengan mudah tanpa memerlukan infrastruktur jaringan yang kompleks.

### Message Broker (RabbitMQ)

![](https://i.imgur.com/pHh2jpi.png)

### _Make it works_

![](https://i.imgur.com/rabjLy3.jpeg)

Setelah menjalankan perintah `cargo run` di direktori subscriber dan publisher, konsol menampilkan bahwa program publisher telah berhasil mengirim lima pesan `UserCreatedEventMessage`. Masing-masing pesan berisi `user_id ` dan  `user_name `, yang mengidentifikasikan pengguna yang dibuat. Pesan-pesan ini dihasilkan secara berurutan, mulai dari `user_id`: "1" hingga `user_id`: "5", menunjukkan bahwa program mampu memproses dan mengirim beberapa pesan secara berurutan. Konsol pada subscriber menunjukkan bahwa pesan telah diterima, yang menandakan komunikasi antara publisher dan subscriber berfungsi dengan baik. Proses ini merupakan inti dari sistem berbasis publikasi dan subscripsi, di mana pesan dikirim dan diterima melalui _message broker_. Keberhasilan pengiriman dan penerimaan ini juga menunjukkan bahwa setup RabbitMQ sudah dikonfigurasi dengan benar dan siap untuk digunakan dalam pengembangan lebih lanjut.