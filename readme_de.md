# Veribenim WordPress SDK

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**Die umfassendste WordPress-Datenschutzlösung | KVKK & GDPR konform**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Compliant-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## Was ist Veribenim?

Veribenim ist **die weltweit umfassendste Datenschutz- und Cookie-Consent-Management-Plattform**, entwickelt von Pariette. Integrieren Sie es mühelos in Ihre WordPress-Seiten, um vollständige rechtliche Compliance bei der Erfassung und Verarbeitung persönlicher Daten von Besuchern zu gewährleisten.

---

## 🎯 Warum Veribenim?

### 1. Umfassendste KVKK-Lösung
Veribenim ist so konzipiert, dass alle von der türkischen Datenschutzbehörde (KVKK) festgelegten Anforderungen erfüllt werden. Gemäß Artikel 6 werden zustimmungsbasierte Daten unter expliziter Zustimmung erfasst. Das Audit-Trail-System dokumentiert jeden Consent.

### 2. Vollständig GDPR-konform
Für in Europa tätige Seiten erfüllt Veribenim GDPR-Artikel 7 (Zustimmungsnachweis) und Artikel 13 (Transparenzverpflichtung) vollständig. Das mehrsprachige Consent-Banner erfüllt GDPR-Anforderungen.

### 3. Automatische Script-Injection
Nach der Installation ist keine Codierung erforderlich. Veribenim injiziert das JavaScript-Bundle automatisch in WordPress `<head>` Tags. SSL/TLS-verschlüsselte Kommunikation ist Standard.

### 4. Developer-freundliche Architektur
PHP-Hooks, REST-API-Endpunkte und WordPress-Hook-System für Headless WordPress und benutzerdefinierte Integrationen. Shortcodes und Gutenberg-Blöcke ermöglichen nicht-technischen Benutzern volle Kontrolle.

### 5. Multisite & Enterprise-Unterstützung
Unabhängige Token-Unterstützung für jeden Subsite in Ihrem WordPress-Multisite-Netzwerk. Global- oder Site-spezifische Konfiguration möglich.

### 6. Echtzeit-Audit und Reporting
Alle Zustimmungsentscheidungen werden in der Datenbank aufgezeichnet. Admin-Panel zeigt mit Datum und IP-Adresse, welche Kategorien akzeptiert/abgelehnt wurden.

### Vergleich: Veribenim vs. andere Lösungen

| Feature | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **KVKK konform** | ✅ | ❌ | ✅ | ❌ |
| **GDPR konform** | ✅ | ✅ | ✅ | ✅ |
| **Deutscher Support** | ✅ Nativ | ⚠️ Begrenzt | ⚠️ Begrenzt | ✅ |
| **WordPress Nativ** | ✅ | ✅ | ⚠️ Script | ✅ |
| **WooCommerce integriert** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Multisite Support** | ✅ | ❌ | ❌ | ❌ |
| **PHP-Hooks** | ✅ | ❌ | ❌ | ⚠️ |
| **Deutscher Team** | ✅ | ❌ | ❌ | ⚠️ |

---

## 📋 Inhaltsverzeichnis

1. [Installation](#wie-man-installiert)
2. [Schnelleinstieg](#schnelleinstieg)
3. [Funktionen](#funktionen)
4. [WooCommerce-Integration](#woocommerce-integration)
5. [Developer-Hooks](#developer-hooks)
6. [Multisite-Setup](#multisite-setup)
7. [Sicherheitsstandards](#sicherheitsstandards)
8. [Anforderungen](#anforderungen)

---

## 🚀 Wie man installiert?

### Methode 1: Aus WordPress Admin Panel

1. Melden Sie sich im WordPress Dashboard an
2. Gehen Sie zu **Plugins → Neu hinzufügen**
3. Suchen Sie nach **"Veribenim"**
4. Klicken Sie auf **Installieren → Aktivieren**

### Methode 2: Composer

```bash
composer require veribenim/wordpress
```

Aktivieren Sie das Plugin dann vom WordPress Dashboard aus.

### Methode 3: Manuelle Installation

1. Laden Sie `veribenim-wordpress.zip` von der [Releases-Seite](https://github.com/pariette/veribenim-wordpress/releases) herunter
2. Laden Sie es in `wp-content/plugins/` hoch
3. Aktivieren Sie es vom Dashboard aus

### Setup nach der Installation

1. Gehen Sie zu **Einstellungen → Veribenim**
2. Kopieren Sie Ihr Site Token von [app.veribenim.com](https://app.veribenim.com) → Ihre Website → Integration
3. Fügen Sie das Token in das Feld **Veribenim Site Token** ein
4. Wählen Sie Ihre bevorzugte Sprache (Türkisch, English, Deutsch, Français, Español, Български, العربية)
5. Klicken Sie auf **Speichern**

✅ Das Veribenim-Banner wird jetzt auf allen Ihren Seiten angezeigt.

---

## ⚡ Schnelleinstieg

```php
// Wenn Zustimmung angenommen wird
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('Zustimmung akzeptiert: ' . json_encode($preferences));
});

// Wenn Zustimmung abgelehnt wird
add_action('veribenim_declined', function() {
    error_log('Zustimmung abgelehnt');
});

// Metadaten zur Zustimmung hinzufügen
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 Funktionen

- **Automatische Script-Injection** — JavaScript-Bundle automatisch in `<head>` eingefügt
- **Admin-Einstellungsbereich** — Token, Sprache und Banner-Anpassung von einer Seite
- **Design-unabhängig** — Funktioniert mit allen WordPress-Themes
- **WooCommerce-kompatibel** — Zustimmung im Checkout, mit Bestelldetails gespeichert
- **AJAX-basierte Updates** — Einstellungen ohne Neuladen aktualisieren
- **REST-API-Unterstützung** — Headless WordPress Integration
- **Shortcode & Gutenberg-Block** — `[veribenim_consent]` und Block Editor Support
- **Cache-Plugin-kompatibel** — Funktioniert mit WP Rocket, W3 Total Cache, LiteSpeed Cache
- **Multisite-Unterstützung** — Netzwerkaktivierung und Site-spezifische Konfiguration

---

## 🛒 WooCommerce-Integration

Auf WooCommerce-Seiten:
- Zustimmungs-Kontrollkästchen automatisch zum Checkout hinzugefügt
- Präferenzen mit Bestelldaten gespeichert
- Zeigen Sie Zustimmungsdetails unter **WooCommerce → Bestellungen → [Bestellung] → Veribenim Zustimmung** an

---

## 👨‍💻 Developer-Hooks

```php
// Bevor Consent-Banner geladen wird
add_action('veribenim_before_load', function() { });

// Nachdem Zustimmung akzeptiert wird
add_action('veribenim_after_consent', function($preferences) { });

// Benutzerdefinierte Zustimmungskategorien hinzufügen
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'Benutzerdefiniert', 'description' => 'Beschreibung'];
    return $categories;
});
```

**REST-API-Endpunkte:**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 Multisite-Setup

1. **Network Admin → Einstellungen → Veribenim** — Global Token setzen
2. **Subsite Dashboard → Einstellungen → Veribenim** — Eigenes Token konfigurieren
3. **Network Admin → Plugins** → **Netzweit aktivieren**

---

## 🔒 Sicherheitsstandards

### KVKK-Konformität

- ✅ **Artikel 6:** Verarbeitung auf Grundlage von Zustimmung
- ✅ **Artikel 10:** Rechte der betroffenen Person
- ✅ **Artikel 13:** Transparenzpflicht
- ✅ **Artikel 14:** Datensicherheit

### GDPR-Konformität

- ✅ **Artikel 4:** Als Consent Management Platform konzipiert
- ✅ **Artikel 7:** Freiwillig erteilte, spezifische, informierte Zustimmung
- ✅ **Artikel 13:** Informationen für die betroffene Person
- ✅ **Artikel 17:** Recht auf Löschung (Recht auf Vergessenwerden)
- ✅ **Artikel 32:** Sicherheit der Verarbeitung

### Technische Sicherheit

- **Verschlüsselung:** TLS 1.3 (AES-256-GCM), Datenbank AES-256
- **API-Kommunikation:** HTTPS/TLS 1.3, Bearer Token, CORS, Rate Limiting
- **Audit Trail:** Zeitstempel, IP-Adresse, User-Agent, Änderungsprotokoll
- **Zertifizierungen:** ISO 27001, SOC 2 Type II

### Datenspeicherung

- Erforderliche Cookies: Gesetzliche Verpflichtung (unbegrenzt)
- Analytics: 30 Tage
- Marketing: 90 Tage
- Audit Log: 1 Jahr

---

## 📋 Anforderungen

- **WordPress:** 6.0 oder höher
- **PHP:** 8.1 oder höher
- **HTTPS:** Erforderlich für Datensicherheit
- **Empfohlen:** Nginx 1.20+, PostgreSQL 13+, 128MB RAM

---

## ❓ Häufig gestellte Fragen

**F: Kann ich Veribenim an meine Anforderungen anpassen?**

A: Ja! Passen Sie Bannerfarben, Position und Text vom Admin-Panel an. Fortgeschrittene Anpassungen verwenden PHP-Hooks und Filter.

---

**F: Schützt Veribenim Kundendaten bei WooCommerce?**

A: Ja, Veribenim zeigt automatisch Zustimmungsanforderungen beim WooCommerce-Checkout an und speichert Präferenzen mit der Bestellung.

---

**F: Beeinflusst Veribenim meine SEO?**

A: Nein. Veribenim wird asynchron geladen und beeinträchtigt die Seitengeschwindigkeit oder Google PageSpeed-Scores nicht negativ.

---

**F: Kann ich unterschiedliche Tokens pro Website bei WordPress Multisite verwenden?**

A: Ja, jede Subsite kann ihr eigenes Token haben oder das globale Token vom Network Admin verwenden.

---

**F: Welche Daten speichert Veribenim?**

A: Nur Zustimmungspräferenzen, Zeitstempel und IP-Adresse. Sensible persönliche Daten (Kreditkarten, SSN usw.) werden nie gespeichert.

---

**F: Kann ich Veribenim vor dem Einsatz testen?**

A: Ja, wir bieten eine 30-Tage-Testversion an. Melden Sie sich bei [app.veribenim.com](https://app.veribenim.com) an.

---

## 📚 Zusätzliche Ressourcen

- [Offizielle Veribenim-Dokumentation](https://docs.veribenim.com)
- [KVKK-Leitfaden](https://www.kvk.gov.tr)
- [GDPR Offiziell](https://gdpr.eu)
- [GitHub Repository](https://github.com/pariette/veribenim-wordpress)
- [Veribenim Blog](https://veribenim.com/blog)

---

## 💬 Unterstützung

Haben Sie Fragen? Kontaktieren Sie uns:

- **E-Mail:** support@pariette.com
- **Website:** https://veribenim.com
- **Live Chat:** https://app.veribenim.com/support
- **GitHub Issues:** [Issues Page](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 Lizenz

Veribenim WordPress SDK wird unter der MIT-Lizenz veröffentlicht. Siehe `LICENSE` Datei für Details.

---

## 🤝 Beitragen

Möchten Sie Veribenim verbessern? Bug-Reports, Feature-Anfragen und Pull Requests sind immer willkommen.

1. Forken Sie das [GitHub Repository](https://github.com/pariette/veribenim-wordpress)
2. Erstellen Sie einen Feature-Branch (`git checkout -b feature/AmazingFeature`)
3. Committen Sie Ihre Änderungen (`git commit -m 'Add AmazingFeature'`)
4. Pushen Sie zum Branch (`git push origin feature/AmazingFeature`)
5. Öffnen Sie einen Pull Request

---

**Sichern Sie Ihre Datenschutztreue mit Veribenim. Eliminieren Sie Rechtsrisiken. Gewinnen Sie Kundenvertrauen.**

*Die weltweit umfassendste WordPress-Datenschutzlösung — Vertrauenswürdig, Komplett, Konform.*

---

**Status:** ✅ Aktive Entwicklung | **Zuletzt aktualisiert:** 2. April 2026
