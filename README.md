<h1 align=center >Alrawi Micro</h1>
<div align=center >
  
![Banner](https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/d8b6ab66-19a2-4b9f-8275-a72ba4667486)
</div>

## Mikroişlemciler için PWM ve Timer Hesaplayıcı

Bu **Flutter** uygulaması, mikroişlemci tabanlı sistemlerdeki `PWM` (Pulse Width Modulation) ve timer için `ARR` (Auto-Reload Register), `PSC` (Prescaler) ve `CCR` (Capture/Compare Register) değerlerini kolayca hesaplamanızı sağlar.

## Özellikler
- ARR Hesaplama: Auto-Reload Register değerini hesaplar.
- PSC Hesaplama: Prescaler değerini hesaplar.
- CCR Hesaplama: PWM için Capture/Compare Register değerini belirler.
- Kullanıcı Dostu Arayüz: Kullanıcı dostu ve sezgisel arayüz.
- Gerçek Zamanlı Güncellemeler: Değerleri girer girmez anında sonuçlar.

## Sayfalar
- Ana Sayfa
- TIM
- PWM

## Ana Sayfa

Ana sayfa, kullanıcıyı karşılayan iki büyük düğmeden oluşur: `TIM` ve `PWM` hesaplamaları için.
<div align=center >
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/5f1eb72e-532a-4c62-b51b-6a71e20b41bc" width = 50%>
</div>

### TIM Sayfası

TIM hesaplama sayfasında, kullanıcılar frekans `Hz` veya periyot `ms` değerlerini girerek ilgili `ARR` ve `PSC` değerlerini hesaplayabilirler. 

Örnek: `10Hz` frekans veya `100ms` periyot için hesaplama.

#### Frekans Girişi (10Hz)

- **Frekans (Hz)**: 10
- **Signal Period (s)**: 1 / 10 = 0.1 saniye
- **Timer Period (ms)**: 0.1 / 2 * 1000 = 50 ms
- **Timer Clock**: 72000
- **Sonuç**: Timer Period * Timer Clock = 50 * 72000 = 3600000

`ARR` ve `PSC` değerleri üzerinde işlem yaparken daha kolay olması için 7200 ile 65536 arasında bir aralıkta hesaplanır. Örneğin, 7200 - i şeklinde bir değeri seçerek, `PSC`'yi aşağıdaki gibi hesaplarız:
- **ARR**: 7200
- **PSC**: 500
- **Zaman Periyodu**: 50 ms

#### Periyot Girişi (100ms)

- **Periyot (ms)**: 100
- **Frekans (Hz)**: 1000 / (100 * 2) = 5 Hz

Aynı frekans hesabı yöntemi kullanılarak `ARR` ve `PSC` değerleri hesaplanabilir:

- **ARR**: 7200
- **PSC**: 1000
- **Zaman Periyodu**: 100 ms
<div align=center >
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/00f29ae2-79b2-4801-a411-390667b0d83f" width = 32% >
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/c62c8bb0-0444-449b-b3be-be7801cc565c" width = 32% >
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/fa7c7961-6f68-462d-93da-ba1094a17669" width = 32% >
</div>

TIM hesaplama işlemi, girilen değere göre ilgili frekans veya periyot değerlerini `ARR` ve `PSC`'ye dönüştürür ve sonucu ekranda gösterir.

### PWM Sayfası

PWM hesaplama sayfasında, kullanıcılar frekans `Hz` ve görev döngüsü `%` değerlerini girerek `ARR`, `PSC` ve `CCR1` değerlerini hesaplayabilirler. 

Örnek: `10Hz` frekans ve `%20` görev döngüsü için hesaplama.

#### Giriş Değerleri: 10Hz, %20

- **Frekans (Hz)**: 10
- **Görev Döngüsü (%)**: 20
- **Signal Period (s)**: 1 / 10 = 0.1 saniye
- **Timer Period (ms)**: 0.1 * 1000 = 100 ms
- **Timer Clock**: 72000
- **Sonuç**: Timer Period * Timer Clock = 100 * 72000 = 7200000

`ARR` ve `PSC` değerleri, 7200 ile 65536 arasında bir aralıkta hesaplanır. Örneğin, 7200 - i şeklinde bir değeri seçerek, `PSC`'yi aşağıdaki gibi hesaplarız:
- **ARR**: 7200
- **PSC**: 1000
- **CCR1**: ARR * Görev Döngüsü = 7200 * 0.2 = 1440
- **Zaman Periyodu**: 100 ms

  
<div align=center >
</div>
<div align=center >
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/0f65d582-c0cd-4384-ae2b-42d4e505d1ae" width = 49%>
  <img src="https://github.com/yasir723/ALRAWI-MICRO/assets/111686779/f1cab403-2827-4b52-adc4-b652929976a3" width = 49%>
</div>

PWM hesaplama işlemi, girilen frekans ve görev döngüsüne göre `ARR`, `PSC` ve `CCR1` değerlerini hesaplar ve sonucu ekranda gösterir.
