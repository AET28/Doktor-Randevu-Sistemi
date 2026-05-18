# Hospital Management Dashboard - Doktor Randevu Sistemi

Hastaların dinamik olarak kayıt edilebildiği, doktorların uzmanlık alanlarına göre listelendiği ve uygun çalışma saatlerine göre randevu planlaması ile iptal süreçlerinin yönetilebildiği modern bir masaüstü sağlık otomasyonudur. Tkinter kütüphanesi üzerinde gece mavisi teması (#0b111b) ve Nesne Yönelimli Programlama (OOP) prensipleri kullanılarak, esnek randevu havuzu mimarisiyle geliştirilmiştir.

---

### 🚀 Teknolojiler

* **Python 3** - Temel programlama dili
* **Tkinter** - Dahili masaüstü GUI (Grafik Kullanıcı Arayüzü) kütüphanesi
* **OOP (Object-Oriented Programming)** - İlişkisel nesne mimarisi ve veri yönetimi

---

### 📂 Proje Yapısı

```text
doktor_randevu_sistemi/
├── backend.py                       # Hasta, Doktor ve Randevu modelleri ile zaman mantığı
└── frontend.py                      # Dashboard arayüzü, dinamik form yönetimi ve iptal pencereleri

🧠 Ana Sınıflar ve Modeller
👤 Hasta (backend.py -> Hasta)

    Özellikler: hasta_id, ad, tc, telefon

🩺 Doktor (backend.py -> Doktor)

    Özellikler: doktor_id, ad, uzmanlik, uygun_saatler (Varsayılan: 09:00, 10:00, 11:00, 14:00, 15:00)

    Metodlar: * uygunluk_kontrol(saat): Seçilen saatin boşta olup olmadığını doğrular.

        randevu_saatini_kullan(saat): Alınan saati doktorun takviminden kaldırır.

        saati_iade_et(saat): İptal edilen saati doktorun takvimine geri ekler ve kronolojik olarak sıralar.

📅 Randevu (backend.py -> Randevu)

    Özellikler: randevu_id (Otomatik artan benzersiz ID), tarih, saat, doktor (Doktor nesnesi), hasta (Hasta nesnesi)

✨ Temel Özellikler

    Merkezi Randevu Paneli (Dashboard): Alınan tüm randevuları Hasta Adı, Doktor, Tarih ve Saat bilgileriyle Treeview üzerinde tablo düzeninde anlık listeler.

    Dinamik Zaman Dilimi Yönetimi: Bir doktora randevu kaydedildiğinde, o saat dilimi doktorun listesinden dinamik olarak silinir; böylece aynı doktora aynı saatte mükerrer (çift) randevu verilmesi engellenir.

    Akıllı Randevu İptal ve Zaman İadesi (Rollback): Listeden seçilen bir randevu iptal edildiğinde, ilgili zaman dilimi otomatik olarak o doktorun uygun saatler havuzuna geri aktarılır ve saat sırasına göre yeniden dizilir.

    Gelişmiş Form Validasyonları: T.C. Kimlik Numarası (11 hane), Telefon Numarası (11 hane) ve boş alan kontrolleri içeren, hatalı veri girişini engelleyen kullanıcı dostu doğrulama mekanizması.

    Modern Gece Mavisi Arayüz: Derin uzay mavisi (#0b111b), kart arka planları (#162031) ve canlı neon mavi vurgu (#3498db) renk paletiyle tasarlanmış, pürüzsüz tipografiye sahip panel tasarımı.

🛠️ Kurulum ve Çalıştırma

Proje, Python'ın standart kütüphanelerini temel aldığı için harici bir bağımlılık (pip install) gerektirmeden doğrudan çalıştırılabilir.

Sistemi başlatmak için terminalde şu komutu yürütmeniz yeterlidir:
Bash

python frontend.py

🌱 Varsayılan Doktor ve Çalışma Verileri

Sistem ilk açıldığında, klinik birimlerin test edilebilmesi amacıyla arka planda otomatik olarak aşağıdaki uzman doktor kadrosunu tanımlar ve kullanıma sunar:

    Dr. Ahmet Yılmaz - Kardiyoloji

    Dr. Elif Kaya - Göz Hastalıkları

    Dr. Can Demir - Dahiliye

    Dr. Yaren Taşkala - Kalp ve Damar Cerrahisi

    Dr. Lujayen Ajahar - Beyin Cerrahisi
