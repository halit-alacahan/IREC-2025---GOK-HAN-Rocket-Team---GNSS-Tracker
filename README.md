# 🛰️ Dual-LoRa High-Altitude GNSS Tracking System (IREC 2025)

An avionic-grade, dual-band telemetry and GNSS tracking board developed for high-altitude sounding rockets and competitive aerospace payloads (IREC 2025).

---

<p align="center">
  <img src="Tracker%20IREC.png" alt="IREC Tracker PCB Preview" width="750">
</p>

---

## 📌 Genel Bakış (Overview)

This board is designed to provide real-time recovery telemetry, positional coordinates, barometric altitude, and power diagnostic monitoring over redundant long-range RF links during sounding rocket flights[cite: 1].

---

## 🛠️ Donanım Mimarisi & Teknik Özellikler (Hardware Specs)

* **Ana İşlemci (MCU):**
  * **STM32F446RET6** (ARM Cortex-M4 @ 180 MHz, DSP + FPU)[cite: 1]
  * Dedicated SWD programming/debugging interface and hardware reset circuitry[cite: 1]

* **RF & Telemetri Haberleşmesi (Dual-Band LoRa):**
  * **LoRa Modül 1:** Ebyte **E22-900M33S** (SPI Arayüzü, 868/915 MHz, +33 dBm / 2W çıkış gücü)[cite: 1]
  * **LoRa Modül 2:** Ebyte **E22-400T37S** (UART Arayüzü, 433/470 MHz, +37 dBm / 5W yüksek güç desteği)[cite: 1]
  * Bağımsız harici SMA/U.FL RF anten konnektörleri[cite: 1]

* **Sensörler ve Konumlandırma (Sensors & Navigation):**
  * **GNSS Modülü:** Quectel **L86 GPS** (Dahili yama anten + harici aktif anten desteği & PPS çıkışı)[cite: 1]
  * **Barometre / Altimetre:** Bosch Sensortec **BME280** (I2C haberleşmeli yüksek hassasiyetli basınç/irtifa/sıcaklık sensörü)[cite: 1]

* **Veri Depolama ve Arayüzler (Storage & Interfaces):**
  * **Flash Bellek:** **W25Q256JV** (256 Mbit / 32 MB High-Speed SPI NOR Flash)[cite: 1]
  * **MicroSD Kart Yuvası:** SPI modunda çalışan tam korumalı SD kart yuvası[cite: 1]
  * **USB-UART Arayüzü:** **FT232RNL** ile doğrudan USB üzerinden telemetri ve hata ayıklama[cite: 1]

* **Güç Yönetimi ve Sensörler (Power Architecture & Diagnostics):**
  * **Buck Regülatör:** **AP63205** (5V / 2A Yüksek verimli senkron anahtarlamalı regülatör)[cite: 1]
  * **LDO Regülatör:** **AMS1117-3.3** (MCU, sensörler ve çevre birimleri için temiz 3.3V rayı)[cite: 1]
  * **Akım & Gerilim İzleme:** **INA139NA** (Yüksek taraf akım algılama şönt amplifikatörü + direnç gerilim bölücü ile batarya takibi)[cite: 1]
  * **Yedek Güç (RTC / Ephemeris Backup):** L86 GPS için harici batarya destek hattı (`V_BCKP`)[cite: 1]
  * **Sesli & Görsel İkaz:** MOSFET sürücülü buzzer ve durum bildirim LED'leri[cite: 1]

---

## 📁 Proje Dosya Yapısı (Repository Structure)

```text
├── Altium PROJECT/          # Altium Designer proje dosyaları (.PrjPcb, .PcbDoc)
├── Altium SCHEMATIC/        # Modüler şematik çizimleri (.SchDoc)
├── GPS_TRACKER_IREC.pdf     # Tam şematik ve donanım çizim dokümanı
├── Tracker IREC.png         # Kart önizleme görseli
└── README.md                # Proje tanıtım ve teknik dokümantasyonu
