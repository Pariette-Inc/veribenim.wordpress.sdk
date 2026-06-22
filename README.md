# Veribenim WordPress SDK

> ℹ️ **Kanonik kaynak:** Veribenim PHP SDK'ları artık tek bir monorepo'da toplanıyor: **`veribenim.php.sdk`** (`packages/wordpress`). Geliştirme orada sürer; bu repo onunla senkron tutulur. Yeni katkıları monorepo'ya gönderin.

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**Türkiye'nin En Kapsamlı WordPress Veri Gizliliği Çözümü | KVKK & GDPR Uyumlu**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Uyumlu-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## Veribenim Nedir?

Veribenim, Pariette tarafından geliştirilen **Türkiye'nin en kapsamlı veri gizliliği ve çerez yönetimi platformu**dur. WordPress sitelerinize kolayca entegre edilerek, ziyaretçilerin kişisel verilerinin toplanması ve işlenmesi konusunda tam yasal uyumluluk sağlar.

---

## 🎯 Neden Veribenim?

### 1. En Kapsamlı KVKK Çözümü
Veribenim, KVKK'nın 6. Madde uyarınca rızaya dayalı veriler açık rız kapsamında toplanır. Audit trail sistemi her konsenti kaydeder.

### 2. GDPR Tam Uyumlu
Avrupa'da faaliyet gösteren siteler için GDPR Madde 7 (Rızanın Kanıtı) tamamen uyumludur. Çok dilli consent banner, GDPR'ın multilingual requirement'ını karşılar.

### 3. Otomatik Script Injection
Kurulum sonrası hiçbir kodlama gerekmez. JavaScript bundle'ını otomatik olarak `<head>` tagsına enjekte eder. SSL/TLS şifreli iletişim standart olarak gelir.

### 4. Developer-Friendly Mimarı
PHP hoşları, REST API endpointleri, shortcodes ve Gutenberg blokları.

### 5. Multisite & Enterprise Desteği
WordPress Multisite'ın her subsitesi için bağımsız token desteği.

### 6. Gerçek Zamanlı Audit ve Raporlama
Tüm consent kararları veritabanında kaydedilir, tarih ve IP adresleriyle raporlanır.

### Karşılaştırma: Veribenim vs. Diğer Çözümler

| Özellik | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **KVKK Uyumlu** | ✅ | ❌ | ✅ | ❌ |
| **GDPR Compliant** | ✅ | ✅ | ✅ | ✅ |
| **Türkçe Destek** | ✅ Native | ⚠️ | ⚠️ | ✅ |
| **WordPress Native** | ✅ | ✅ | ⚠️ Script | ✅ |
| **WooCommerce Entegre** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Multisite Destek** | ✅ | ❌ | ❌ | ❌ |
| **PHP Hoşları** | ✅ | ❌ | ❌ | ⚠️ |
| **Türkçe Ekip** | ✅ | ❌ | ❌ | ⚠️ |

### 7. Uçtan Uca KVKK Yönetim Platformu

Veribenim sadece bir çerez eklentisi değil, **tam kapsamlı bir KVKK/GDPR uyum yönetim platformu**dur:

| Modül | Açıklama |
|-------|----------|
| **Veri Hakkı Talepleri (DSAR)** | KVKK Md.11 / GDPR Md.15-22: 7 talep tipi, otomatik 30 gün deadline |
| **Veri İhlali Yönetimi** | GDPR Md.33: 72 saat countdown, risk seviyesi, otorite bildirim kaydı |
| **VERBİS / RoPA Export** | KVKK VERBİS kaydı ve GDPR Md.30 RoPA: CSV/JSON export, 17 alan |
| **Politika Yönetimi** | Gizlilik politikası, çerez politikası, KVKK aydınlatma — çoklu dil, PDF/HTML export |
| **Uyumluluk Skoru** | 22 kural, 5 kategori, A-F notlandırma, düzeltme önerileri |
| **Form Rızası Takibi** | İletişim, üyelik formlarındaki KVKK onayını kayıt altına alma |
| **Webhook Sistemi** | 7 olay tipi, HMAC-SHA256, Slack/Teams/n8n entegrasyonu |
| **Çerez Tarayıcı** | 50+ bilinen tracker otomatik tespiti |
| **Tercih Merkezi** | Kalıcı panel + DSAR entegrasyonu |
| **Veri Envanteri** | KVKK Md.16 / GDPR Md.30: Departman ve süreç bazlı veri haritalama, 20 veri kategorisi, VERBİS uyumlu export |
| **Saklama-İmha Otomasyonu** | KVKK Md.7 / GDPR Md.17: Saklama politikaları, otomatik imha, imha tutanakları, 5 imha yöntemi |
| **Risk Yönetimi** | KVKK Md.12 / GDPR Md.35: 5x5 risk matrisi, 7 risk kategorisi, aksiyon takibi, risk raporu export |
| **İç Denetim & Aksiyon Takibi** | 6 denetim tipi, 0-100 puanlama, aksiyon atama ve gecikme takibi |
| **Doküman Şablonları** | 10 hazır KVKK/GDPR şablonu, değişken sistemi, çoklu dil, versiyon takibi |
| **Rıza Versiyonlama** | Onay metni versiyon takibi, yeniden onay mekanizması, versiyon karşılaştırma |
| **AI Asistan** | RAG tabanlı KVKK/GDPR bilgi asistanı |
| **Meşru Menfaat Değerlendirmesi (LIA)** | KVK Kurul rehberi uyumlu 3-adım balans testi: Amaç → Zorunluluk → Dengeleme |
| **VERBİS Kayıt Asistanı** | KVKK Md.16: 50+ çalışan eşiği kontrolü, veri işleme aktivitesi kayıt ve export |
| **Rıza Yenileme** | KVK Kurul Çerez Rehberi 2022: 12 aylık zorunlu yenileme, otomatik banner tetikleme |
| **Rızayı Geri Çekme** | KVKK Md.11/1-e: `withdraw` aksiyonu, WP action hook ile entegrasyon |
| **Veri Saklama & İmha** | KVKK Md.7: Ortam bazlı saklama süreleri, otomatik periyodik imha |
| **Çerez Duvarı Koruması** | KVK Kurul kararı: Cookie wall yasağı, compliance score denetimi |

---

## 📋 İçindekiler

1. [Kurulum](#nasıl-kurulur)
2. [Hızlı Başlangıç](#hızlı-başlangıç)
3. [Özellikler](#özellikler)
4. [WooCommerce Entegrasyonu](#woocommerce-entegrasyonu)
5. [Developer Hoşları](#developer-hoşları)
6. [Multisite Kurulumu](#multisite-kurulumu)
7. [Güvenlik Standartları](#güvenlik-standartları)
8. [Gereksinimler](#gereksinimler)

---

## 🚀 Nasıl Kurulur?

### Yöntem 1: WordPress Admin Panelinden

1. WordPress Dashboard'a giriş yapın
2. **Eklentiler → Yeni Ekle**'ye tıklayın
3. Arama kutusuna **"Veribenim"** yazın
4. **Yükle → Etkinleştir**'e tıklayın

### Yöntem 2: Composer

```bash
composer require veribenim/wordpress
```

### Yöntem 3: Manual

1. [Releases sayfasından](https://github.com/pariette/veribenim-wordpress/releases) zip dosyasını indirin
2. `wp-content/plugins/` dizinine upload edin
3. Dashboard'da etkinleştirin

### Kurulum Sonrası Yapılandırma

1. **Ayarlar → Veribenim**'e gidin
2. Site Token'ınızı [app.veribenim.com](https://app.veribenim.com) → Siteniz → Entegrasyon bölümünden kopyalayın
3. Token'ı yapıştırın
4. Dil tercihini seçin (Türkçe, English, Deutsch, Français, Español, Български, العربية)
5. **Kaydet**'e tıklayın

✅ Veribenim banner'ı tüm sayfalarınızda görünecektir.

---

## ⚡ Hızlı Başlangıç

```php
// Consent kabul edildiğinde
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('Consent kabul edildi: ' . json_encode($preferences));
});

// Consent reddedildiğinde
add_action('veribenim_declined', function() {
    error_log('Consent reddedildi');
});

// Meta verisi eklemek
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 Özellikler

- **Otomatik Script Injection** — JavaScript bundle otomatik `<head>` bölümüne eklenir
- **Admin Ayarları Paneli** — Token, dil ve banner özelleştirmesi
- **Theme-Bağımsız Tasarım** — Tüm WordPress temalarıyla uyumlu
- **WooCommerce Uyumluluğu** — Checkout'da consent, sipariş detaylarında kaydı
- **AJAX-Tabanlı Güncellemeler** — Sayfayı yeniden yüklemeden tercih güncelleme
- **REST API Desteği** — Headless WordPress entegrasyonu
- **Shortcode & Gutenberg Block** — `[veribenim_consent]` ve block editor desteği
- **Caching Plugin Uyumluluğu** — WP Rocket, W3 Total Cache ile uyumlu
- **Multisite Desteği** — Network activation ve site-bazlı yapılandırma
- **Rıza Geri Çekme Hook** — `veribenim_consent_withdrawn` aksiyonu ile entegrasyon
- **Rıza Yenileme** — 12 aylık zorunlu yenileme, banner otomatik tetikleme
- **Çerez Duvarı Engeli Yok** — KVK Kurul kararına uygun, siteye erişim kısıtlanmaz

---

## 🛒 WooCommerce Entegrasyonu

WooCommerce sitelerinizde:
- Checkout formunda consent checkbox'ı otomatik eklenir
- Sipariş tercihlerini kaydeder
- Admin panelinde **WooCommerce → Siparişler → [Sipariş] → Veribenim Onayı** sekmesinde görüntülenir

---

## 👨‍💻 Developer Hoşları

```php
// Consent banner yüklenmeden önce
add_action('veribenim_before_load', function() { });

// Consent kabul edildikten sonra
add_action('veribenim_after_consent', function($preferences) { });

// Rıza geri çekildiğinde (KVKK Md.11/1-e)
add_action('veribenim_consent_withdrawn', function($session_id) {
    // Kullanıcı verilerini işlemeyi durdur
    error_log("Consent withdrawn for session: {$session_id}");
});

// Rıza yenileme gerektiğinde
add_action('veribenim_renewal_required', function($session_id) {
    // Banner'ı yeniden göster
});

// Custom kategoriler eklemek
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'Özel', 'description' => 'Açıklama'];
    return $categories;
});
```

**REST API:**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 Multisite Kurulumu

1. **Network Admin → Settings → Veribenim** — Global token ayarlama
2. **Subsite Dashboard → Settings → Veribenim** — Kendi token'ı konfigüre etme
3. **Network Admin → Plugins** → **Network Activate**

---

## 🔒 Güvenlik Standartları

### KVKK Uyumluluğu

- ✅ **Madde 5:** Kişisel verilerin işlenme şartları
- ✅ **Madde 6:** Rızaya dayalı veri işleme
- ✅ **Madde 7:** Kişisel verilerin silinmesi ve imhası (periyodik imha)
- ✅ **Madde 10:** Veri sahibinin hakları
- ✅ **Madde 11/1-e:** Rızayı her zaman geri çekme hakkı
- ✅ **Madde 12:** Veri güvenliği
- ✅ **Madde 16:** VERBİS kaydı
- ✅ **KVK Kurul Çerez Rehberi 2022:** Cookie wall yasağı, 12 aylık yenileme, ön işaretli kutu yasağı

### GDPR Uyumluluğu

- ✅ **Madde 4:** Consent Management Platform tasarımı
- ✅ **Madde 7:** Rızanın verilmesi koşulları
- ✅ **Madde 13:** Bilgilendirilme yükümlülüğü
- ✅ **Madde 17:** Silinme hakkı (Unutulma Hakkı)
- ✅ **Madde 32:** Veri güvenliği

### Teknik Güvenlik

- **Şifreleme:** TLS 1.3 (AES-256-GCM), veritabanı AES-256
- **API İletişimi:** HTTPS/TLS 1.3, Bearer Token, CORS, Rate Limiting
- **Audit Trail:** Timestamp, IP, User-Agent, değişiklik tarihi
- **Sertifikalar:** ISO 27001, SOC 2 Type II

### Veri Saklama

- Gerekli Çerezler: Yasal zorunluluk
- Analytics: 30 gün
- Marketing: 90 gün
- Audit Log: 1 yıl

---

## 📋 Gereksinimler

- **WordPress:** 6.0+
- **PHP:** 8.1+
- **HTTPS:** Zorunlu
- **Tavsiye:** Nginx 1.20+, PostgreSQL 13+, 128MB RAM

---

## 💬 Destek

- **E-Mail:** support@pariette.com
- **Website:** https://veribenim.com
- **Live Chat:** https://app.veribenim.com/support
- **GitHub:** [Issues](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 Lisans

MIT © [Pariette](https://veribenim.com)

---

**Veribenim ile veri gizliliğinizi sağlayın. KVKK & GDPR tam uyumlu.**
