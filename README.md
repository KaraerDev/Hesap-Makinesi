# 🧮 Bilimsel Hesap Makinesi 

Tek dosyalık, offline çalışan bilimsel hesap makinesi. Kendi HTML sitene 2 dakikada eklenir. Dark + Light tema destekli, 4 sekmeli.

## ✨ Özellikler

- **4 Sekme:**
  - **Hesap Makinesi:** temel + bilimsel (sin cos tan, asin-acos-atan, sinh cosh tanh, log ln log2, sqrt cbrt, x² x³ xʸ, 10ˣ eˣ, 1/x, |x|, n!, mod, EXP, π e φ τ, Ans, %, +/-, parantez)
  - **Yeni:** nCr nPr (kombinasyon-permütasyon), gcd/lcm (EBOB/EKOK), root(y,n) genel kök, logb(x,taban), klasik yüzde (50+10%=55), S-D kesir butonu (0,333 → 1/3), 🔗 Paylaş butonu (?q= linki)
  - **Birim Çevirici:** Uzunluk, Ağırlık, Sıcaklık, Alan, Hacim, Zaman, Hız, Basınç, Enerji
  - **Programcı:** BIN/OCT/DEC/HEX senkron çeviri + AND OR XOR NOT + kaydırma
  - **Denklem:** ax²+bx+c=0 (delta + reel/çift/kompleks kök), a=0 ise ax+b=0 çözer
- **DEG/RAD, F-E (bilimsel gösterim), FIX 0-9 basamak ayarı**
- **Hafıza:** MC MR M+ M- MS
- **Geçmiş:** son 30 işlem, localStorage, tıklayınca geri yükle, tekli sil + tümünü temizle, kopyala butonu
- **Türkçe uyumu:** `3,14` yazabilirsin, otomatik `3.14` anlaşılır
- **Klavye:** 0-9 + - * / % ^ ( ) . , Enter(=) Backspace Escape
- **Tek dosya, sıfır bağımlılık:** CDN yok, eval() yok (güvenli parser)

## 📁 Dosyalar

```
proj1/
├── calculator.html   # HER ŞEY BURADA — siteye bunu ekle
└── README.md         # bu dosya
```

Çift tıkla `calculator.html` tarayıcıda açılır. Sunucu gerekmez.

## 🚀 Siteye Ekleme (kendi HTML siten için)

### Yöntem 1: Ayrı sayfa (ÖNERİLEN — en temiz)

1. `calculator.html` dosyasını sitene kopyala:
```
benim-sitem/
├── index.html
├── calculator.html   <-- buraya
```
2. Menüye link ekle:
```html
<nav>
  <a href="index.html">Anasayfa</a>
  <a href="calculator.html">Hesap Makinesi</a>
</nav>
```

### Yöntem 2: iframe ile gömme (anasayfada kutu içinde)

```html
<div style="max-width:480px;margin:0 auto;padding:12px;">
  <iframe
    src="calculator.html"
    width="440" height="650"
    loading="lazy"
    sandbox="allow-scripts"
    title="Bilimsel Hesap Makinesi"
    style="width:100%;height:650px;border:0;border-radius:16px;display:block;overflow:hidden;">
  </iframe>
</div>
```

### Yöntem 3: Direkt bölüm olarak gömme

`calculator.html` içindeki `<style>` bloğunu kendi sayfanın `<head>`ine, `<div class="app">` bloğunu `<body>` içine, `<script>` bloğunu `</body>` öncesine kopyala.

## ⌨️ Klavye

| Tuş | İş |
|---|---|
| 0-9 + - * / % ^ ( ) . , ! | giriş |
| Enter / = | hesapla |
| Backspace | sil |
| Escape | temizle (AC) |

## ❓ Sık Sorunlar

1. **sin(30) yanlış?** → DEG/RAD butonunu kontrol et. Okul matematiği = DEG.
2. **Virgül?** → `3,14` yazabilirsin. `1.000,50` yazma, `1000,50` yaz.
3. **Mobil taşma?** → `meta viewport` olmalı + iframe sarmalayıcı kullan.
4. **iframe'de tema hatırlanmıyor?** → sandbox localStorage'ı engeller, normaldir. Kalıcı tema için Yöntem 1'i kullan.
5. **Sıfıra bölme / log(negatif)?** → Türkçe hata mesajı verir, kilitlenmez. AC ile devam et.

## 🔒 Güvenlik

- `eval()` yok, özel tokenizer + recursive-descent parser var.
- CDN yok, offline çalışır.
- Geçmiş sadece senin tarayıcında (localStorage), sunucuya gitmez.
