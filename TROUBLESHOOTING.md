# Sorun Giderme Rehberi

## Veri Görünmüyor Sorunu

Eğer uygulamada içerik görünmüyorsa, aşağıdaki adımları izleyin:

### 1. LocalStorage'ı Temizle

Tarayıcı konsolunu açın (F12) ve şunu çalıştırın:

```javascript
// Tüm FitEco verilerini temizle
['fiteco_users', 'fiteco_products', 'fiteco_orders', 'fiteco_programs', 'fiteco_passes', 'fiteco_reviews', 'fiteco_messages', 'fiteco_campaigns', 'fiteco_cart'].forEach(key => localStorage.removeItem(key));
location.reload();
```

### 2. Sayfayı Yenile

Ctrl+F5 veya Cmd+Shift+R ile hard refresh yapın.

### 3. Veriyi Manuel Yükle

Konsolda şunu çalıştırın:

```javascript
// Veriyi zorla yükle
import('./src/utils/initData.js').then(m => m.initializeSampleData());
location.reload();
```

### 4. Store Durumunu Kontrol Et

Konsolda şunu çalıştırarak store durumunu kontrol edin:

```javascript
// Store durumunu kontrol et
console.log('Users:', JSON.parse(localStorage.getItem('fiteco_users') || '{}'));
console.log('Products:', JSON.parse(localStorage.getItem('fiteco_products') || '{}'));
```

## Animasyonlar Çalışmıyor

1. **Framer Motion yüklü mü kontrol edin:**
   ```bash
   npm list framer-motion
   ```

2. **Eğer yüklü değilse:**
   ```bash
   npm install framer-motion
   ```

3. **Tarayıcı konsolunda hata var mı kontrol edin**

## CSS Efektleri Görünmüyor

1. **Tailwind CSS derleniyor mu kontrol edin**
   - `npm run dev` çalışıyor olmalı
   - CSS dosyaları import edilmiş olmalı

2. **Dark mode aktif mi kontrol edin**
   - Sağ üstteki güneş/ay ikonuna tıklayın

3. **Tarayıcı cache'ini temizleyin**
   - Ctrl+Shift+Delete ile cache temizleyin

## Genel Sorunlar

### Port Çakışması
Eğer port 5173 kullanılıyorsa, Vite otomatik olarak 5174'e geçer. URL'yi kontrol edin.

### Node Modules Sorunu
```bash
rm -rf node_modules package-lock.json
npm install
```

### TypeScript Hataları
```bash
npm run build
```
Hataları kontrol edin ve düzeltin.

