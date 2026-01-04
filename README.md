# FitEco - Spor Ekosistemi Platformu

FitEco, sporcuları ve hizmet sağlayıcılarını (Spor Salonları, PT'ler, Ekipman Satıcıları) bir araya getiren premium bir SaaS platformudur.

## Özellikler

- 🛒 **E-Ticaret**: Ürün kataloğu, sepet yönetimi, sipariş takibi
- 📅 **Randevu Yönetimi**: Antrenör-öğrenci ilişkisi ve program yönetimi
- 📱 **QR Giriş Sistemi**: Spor salonu üyelikleri için QR kod kontrolü
- 🤖 **AI Danışmanlık**: Google Gemini ile akıllı ürün önerileri ve antrenman programı oluşturma
- 💬 **Mesajlaşma**: Kullanıcılar arası iletişim
- 💰 **Cüzdan Sistemi**: Bakiye yükleme ve ödeme yönetimi
- 👥 **Çoklu Rol**: Müşteri, Sağlayıcı, Yönetici arayüzleri

## Teknoloji Yığını

- **React 19**: Modern UI framework
- **TypeScript**: Tip güvenliği
- **Tailwind CSS**: Utility-first CSS framework (Dark mode, Glassmorphism 2.0)
- **Vite**: Hızlı build tool
- **Framer Motion**: Sinematik animasyonlar ve sayfa geçişleri
- **Google Gemini API**: AI entegrasyonu
- **React Router**: Sayfa yönlendirme
- **use-sound**: Mikro etkileşim ses efektleri
- **LocalStorage**: Veri kalıcılığı (MVP için)

## Premium Özellikler

### 🎬 Sinematik Animasyonlar
- **Framer Motion** ile sayfa geçiş animasyonları
- **Layout Animations**: Netflix tarzı kart büyütme efektleri
- **Scroll Reveal**: Sayfa kaydırma sırasında içerik animasyonları
- **Staggered Animations**: Liste öğelerinin sıralı gelişi

### ✨ Glassmorphism 2.0
- **Noise Texture**: Cam yüzeylere film grain efekti
- **Mesh Gradients**: Hareket eden, birbirine karışan renkler
- **Light Reflections**: Mouse hareketine göre ışık yansımaları
- **Premium Glass**: Gelişmiş blur ve saturasyon efektleri

### 🎨 Gelişmiş Dark Mode
- Derinlik katmanları (Surface-100, Surface-200, Surface-300)
- Antrasit tonları ile göz yorgunluğu azaltma
- Mesh gradient arka planlar

### ⚡ Performans Optimizasyonları
- **Skeleton Loading**: Nike tarzı yükleme animasyonları
- **Lazy Loading**: Görsellerin optimize edilmiş yüklenmesi
- **Smooth Scrolling**: Akıcı sayfa kaydırma

## Kurulum

### Gereksinimler

- Node.js 18+ 
- npm veya yarn

### Adımlar

1. **Bağımlılıkları yükleyin:**
   ```bash
   npm install
   ```

2. **Google Gemini API Key'i ayarlayın:**
   
   `.env` dosyası oluşturun:
   ```env
   VITE_GEMINI_API_KEY=your_api_key_here
   ```
   
   API key'i almak için: [Google AI Studio](https://makersuite.google.com/app/apikey)

3. **Geliştirme sunucusunu başlatın:**
   ```bash
   npm run dev
   ```

4. **Tarayıcıda açın:**
   ```
   http://localhost:5173
   ```

## Google AI Studio Sistem Talimatları

AI'ın tutarlı yanıt vermesi için Google AI Studio'da "Sistem Talimatları" bölümüne aşağıdaki talimatı yapıştırın:

```
Sen "FitEco" adında, sporcuları ve hizmet sağlayıcıları (Spor Salonları, PT'ler, Ekipman Satıcıları) bir araya getiren premium bir platformun Yapay Zeka Çekirdeğisin.

GÖREVLERİN:
1. **Satış Asistanı (Recommendation Engine):** Kullanıcının serbest metin olarak girdiği hedefleri (örn: "Kilo vermek istiyorum, dizim ağrıyor") analiz et ve mevcut ürün kataloğundan en uygun ürünleri bir paket (bundle) haline getir.
2. **Antrenör (Workout Generator):** Kullanıcının seviyesine, gün sayısına ve hedefine göre haftalık, detaylı antrenman programı oluştur.
3. **Ürün Uzmanı (QA):** Bir ürünün teknik detayları verildiğinde, müşteri sorularını satış odaklı ve kısa şekilde yanıtla.

KURALLAR:
- Dil: Daima Türkçe konuş.
- Ton: Profesyonel, motive edici, spor terminolojisine hakim ancak anlaşılır.
- Format: Eğer kullanıcıdan yapılandırılmış veri isteniyorsa (öneri veya program gibi), yanıtı SADECE geçerli bir JSON bloğu olarak ver. Markdown veya ek açıklama yapma.

VERİ YAPILARI (JSON SCHEMA):

A) Ürün Önerisi İstendiğinde:
{
  "bundleName": "String (Paket için yaratıcı bir isim)",
  "reasoning": "String (Neden bu ürünleri seçtiğine dair kısa açıklama)",
  "suggestedProductIds": ["String (Ürün ID'leri array'i)"],
  "totalPriceEstimate": Number (Tahmini toplam fiyat)
}

B) Antrenman Programı İstendiğinde:
{
  "title": "String (Program Adı)",
  "notes": "String (Motivasyon notu)",
  "tasks": [
    {
      "day": "String (Pazartesi, Salı...)",
      "name": "String (Hareket detayları, set x tekrar)",
      "isCompleted": false
    }
  ]
}
```

## Proje Yapısı

```
src/
├── components/          # Yeniden kullanılabilir bileşenler
│   ├── Layout.tsx
│   ├── ChatDrawer.tsx
│   ├── ProfileModal.tsx
│   ├── ProductDetailModal.tsx
│   └── AIAdvisorModal.tsx
├── views/              # Sayfa görünümleri
│   ├── customer/       # Müşteri arayüzleri
│   ├── provider/       # Sağlayıcı arayüzleri
│   └── admin/          # Yönetici arayüzleri
├── store/              # State management
│   └── store.ts        # Custom store (useSyncExternalStore)
├── services/           # API servisleri
│   └── ai.ts           # Gemini API entegrasyonu
├── types/              # TypeScript type tanımları
│   └── index.ts
└── utils/              # Yardımcı fonksiyonlar
    └── initData.ts     # Örnek veri başlatma
```

## Kullanım

### Varsayılan Kullanıcılar

Uygulama başlatıldığında örnek kullanıcılar oluşturulur:

- **Müşteri**: ahmet@example.com
- **Sağlayıcı**: fitness@example.com
- **Yönetici**: admin@example.com

### Roller

- **Müşteri (Customer)**: Ürün satın alma, antrenman programı görüntüleme, cüzdan yönetimi
- **Sağlayıcı (Provider)**: Ürün yönetimi, sipariş takibi, öğrenci yönetimi, QR giriş kontrolü
- **Yönetici (Admin)**: Kullanıcı yönetimi, doğrulama onayları, kampanya oluşturma

## Production Roadmap

Mevcut sürüm MVP (Minimum Viable Product) seviyesindedir. Production için:

- [ ] Backend API (Node.js/NestJS + PostgreSQL)
- [ ] Gerçek zamanlı özellikler (WebSockets)
- [ ] Güvenli kimlik doğrulama (Auth0/Firebase)
- [ ] Ödeme entegrasyonu (İyzico/Stripe)
- [ ] Medya yükleme servisi (AWS S3/Cloudinary)
- [ ] SEO optimizasyonu (Next.js SSR)

## Lisans

Bu proje demo amaçlıdır.

