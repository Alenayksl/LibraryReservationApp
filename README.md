# LibraryReservationApp - Kütüphane Rezervasyon Uygulaması

Bu proje, Next.js tabanlı çok dilli (i18n destekli) modern bir kütüphane rezervasyon sistemidir. Kullanıcılar, oturum açarak belirli tarih ve saat aralıklarında müsait odaları görüntüleyebilir, rezervasyon oluşturabilir, güncelleyebilir ve silebilir. Proje, TypeScript, SWR, Zustand, JWT ve uluslararasılaştırma desteği ile geliştirilmiştir.

# Özellikler

-  Çok dilli destek (Türkçe ve İngilizce)
-  JWT tabanlı kullanıcı doğrulama
-  Tarih ve saat seçimiyle oda rezervasyonu
-  Kullanıcıya özel rezervasyon geçmişi ve düzenleme/silme işlemleri
-  Oda isimlerinin dile göre dinamik gösterimi
-  SWR ile veri önbellekleme ve sayfalama
-  Responsive ve kullanıcı dostu arayüz

# Bağlı Backend

Bu frontend projesi, aşağıdaki Node.js tabanlı API servisi ile entegre çalışmaktadır:

👉 [randevusist-Api GitHub Sayfası](https://github.com/esmanurgokkaya/randevusist-Api)

Frontend tarafının düzgün çalışabilmesi için ilgili API'nin çalışır durumda olması gereklidir.

API'nin çalıştığı adres `.env.local` dosyasında aşağıdaki gibi belirtilmelidir:

```env
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```
# Kurulum
Bu repoyu klonlayın:

```
git clone https://github.com/Alenayksl/LibraryReservationApp.git
cd LibraryReservationApp
```
Gerekli bağımlılıkları yükleyin:

```
npm install
```
.env.local dosyasını oluşturun ve aşağıdaki içeriği ekleyin:

```
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```
Geliştirme sunucusunu başlatın:

```
npm run dev
```
# Uluslararasılaştırma (i18n)
Proje, next-intl kütüphanesi ile çoklu dil desteği sağlamaktadır. Desteklenen diller:

tr - Türkçe (varsayılan)

en - İngilizce

Dil değişimi kullanıcı panelinden yapılabilir.

# Durum Yönetimi
Kullanıcı oturumu ve kullanıcı bilgileri Zustand kullanılarak yönetilmektedir. Veriler localStorage ile kalıcı hale getirilmiştir.

# Kimlik Doğrulama
Giriş yapan kullanıcının JWT accessToken ve refreshToken bilgileri cookie olarak saklanır.

Middleware ile korunan rotalara erişim kontrolü sağlanır (/reserve, /reservegor, /profile).

Token bulunmuyorsa kullanıcı giriş sayfasına yönlendirilir.

# 📁 Proje Yapısı (Özet)

📁 app                    → Uygulama sayfaları (Next.js App Router yapısı)
 ┣ 📁 (auth)              → Giriş ve kayıt işlemleri (login, register)
 ┣ 📁 dashboard           → Kullanıcı ana sayfası
 ┣ 📁 login               → Giriş sayfası
 ┣ 📁 register            → Kayıt olma sayfası
 ┣ 📁 reserve             → Rezervasyon oluşturma
 ┣ 📁 reservegor          → Mevcut rezervasyonları görüntüleme/güncelleme
 ┣ 📄 layout.tsx          → Global layout bileşeni
 ┗ 📄 page.tsx            → Giriş sayfası (root `/`)

📁 components             → Ortak bileşenler
 ┣ 📄 LanguageSwitcher.tsx → Dil değiştirme bileşeni
 ┗ 📄 MyButton.tsx         → Özel buton bileşeni

📁 constants              → Sabit değerler
 ┗ 📄 endpoints.ts         → API endpoint sabitleri

📁 hooks                 → Custom React hook’lar
 ┣ 📄 useAuth.ts
 ┣ 📄 usePaginatedReservations.ts
 ┗ 📄 useReservationActions.ts

📁 lib                   → Yardımcı kütüphaneler / API işlemleri
 ┣ 📄 api.ts
 ┗ 📄 auth.ts

📁 stores                → Zustand store dosyaları
 ┗ 📄 authStore.ts

📁 styles                → Global ve modül bazlı stiller
 ┣ 📄 Button.module.scss
 ┗ 📄 globals.scss

📁 types                 → Tip tanımları (TypeScript)
 ┣ 📄 reservation.ts
 ┣ 📄 room.ts
 ┗ 📄 user.ts

📁 utils                 → Yardımcı fonksiyonlar
 ┗ 📄 cookies.ts

📁 i18n                  → Dil desteği ve konfigürasyon
 ┣ 📄 i18n-config.ts
 ┗ 📁 messages           → TR/EN çeviri mesajları

📁 public                → Statik dosyalar (resimler, favicon, vs.)
 ┣ 📄 favicon.ico
 ┣ 📄 globe.svg
 ┣ 📄 vercel.svg
 ┣ 📄 window.svg
 ┗ 📄 file.svg

📄 .eslintrc.json        → Linter ayarları  
📄 middleware.ts         → Next.js middleware dosyası  
📄 next.config.js        → Next.js konfigürasyonu  
📄 package.json          → Bağımlılıklar ve script'ler  
📄 tsconfig.json         → TypeScript yapılandırması  

# Sayfa Görünümleri

![Login Sayfası](./public/assets/login.jpg)
![Home Sayfası](./public/assets/register.jpg)
![Home Sayfası](./public/assets/home.jpg)
![Giriş yapıldıktan sonraki Home Page](./public/assets/dashboard.jpg)
![Rezervasyon Yapma Sayfası](./public/assets/reserve.jpg)
![Mevcut Rezervasyonlar Sayfası](./public/assets/reservegor.jpg)
![Settings butonu ile rezervasyonu update veya silme](./public/assets/reserveupdate.jpg)
![Profil Düzenleme](./public/assets/profile.jpg)

# Hazırlayan: Aleyna Yüksel
