# Veribenim WordPress SDK

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**The Most Comprehensive WordPress Data Privacy Solution | KVKK & GDPR Compliant**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Compliant-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## What is Veribenim?

Veribenim is the **world's most comprehensive data privacy and cookie consent management platform**, developed by Pariette. Easily integrate it into your WordPress sites to ensure complete legal compliance regarding visitor personal data collection and processing.

---

## 🎯 Why Veribenim?

### 1. Most Comprehensive KVKK Solution
Veribenim is designed to meet all requirements set by the Turkish Personal Data Protection Authority (KVKK). According to Article 6, consent-based data is collected and managed within explicit consent scope. The audit trail system records every consent for full traceability.

### 2. Fully GDPR Compliant Architecture
For sites operating in Europe, GDPR Article 7 (Proof of Consent) and Article 13 (Transparency Obligations) are fully satisfied. The multilingual consent banner meets GDPR's multilingual requirements.

### 3. Automatic Script Injection
No coding required after installation. Veribenim automatically injects the JavaScript bundle into WordPress `<head>` tags. SSL/TLS encrypted communication is standard.

### 4. Developer-Friendly Architecture
PHP hooks, REST API endpoints, and WordPress hook system support headless WordPress and custom integrations. Shortcodes and Gutenberg blocks empower non-technical users.

### 5. Multisite & Enterprise Support
Independent token support for each subsite in your WordPress Multisite network. Global configuration from network admin or site-specific customization possible.

### 6. Real-Time Audit and Reporting
All consent decisions are recorded in the database. Admin panel reports consent categories accepted/declined by visitors with dates and IP addresses.

### Comparison: Veribenim vs. Other Solutions

| Feature | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **KVKK Compliant** | ✅ | ❌ | ✅ | ❌ |
| **GDPR Compliant** | ✅ | ✅ | ✅ | ✅ |
| **Native Turkish Support** | ✅ | ⚠️ Limited | ⚠️ Limited | ✅ |
| **WordPress Native** | ✅ | ✅ | ⚠️ Script | ✅ |
| **WooCommerce Integrated** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Multisite Support** | ✅ | ❌ | ❌ | ❌ |
| **PHP Hooks** | ✅ | ❌ | ❌ | ⚠️ |
| **Native Turkish Team** | ✅ | ❌ | ❌ | ⚠️ |

---

## 📋 Table of Contents

1. [Installation](#how-to-install)
2. [Quick Start](#quick-start)
3. [Features](#features)
4. [WooCommerce Integration](#woocommerce-integration)
5. [Developer Hooks](#developer-hooks)
6. [Multisite Setup](#multisite-setup)
7. [Security Standards](#security-standards)
8. [Requirements](#requirements)

---

## 🚀 How to Install?

### Method 1: From WordPress Admin Panel

1. Log in to WordPress Dashboard
2. Go to **Plugins → Add New**
3. Search for **"Veribenim"**
4. Click **Install → Activate**

### Method 2: Composer

```bash
composer require veribenim/wordpress
```

Then activate the plugin from WordPress Dashboard.

### Method 3: Manual Installation

1. Download `veribenim-wordpress.zip` from [releases page](https://github.com/pariette/veribenim-wordpress/releases)
2. Upload to `wp-content/plugins/`
3. Activate from Dashboard

### Post-Installation Setup

1. Go to **Settings → Veribenim**
2. Copy your Site Token from [app.veribenim.com](https://app.veribenim.com) → Your Site → Integration
3. Paste the token in the **Veribenim Site Token** field
4. Select your preferred language (Turkish, English, German, French, Spanish, Bulgarian, Arabic)
5. Click **Save**

✅ The Veribenim banner will now appear on all your pages.

---

## ⚡ Quick Start

```php
// When consent is accepted
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('Consent accepted: ' . json_encode($preferences));
});

// When consent is declined
add_action('veribenim_declined', function() {
    error_log('Consent declined');
});

// Add metadata to consent
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 Features

- **Automatic Script Injection** — JavaScript bundle automatically injected into `<head>` section
- **Admin Settings Panel** — Token, language, and banner customization from one page
- **Theme-Independent Design** — Works with all WordPress themes
- **WooCommerce Compatible** — Consent in checkout, stored with order details
- **AJAX-Based Updates** — Update preferences without page reload
- **REST API Support** — Headless WordPress integration endpoints
- **Shortcode & Gutenberg Block** — `[veribenim_consent]` shortcode and block editor support
- **Caching Plugin Compatible** — Works with WP Rocket, W3 Total Cache, LiteSpeed Cache
- **Multisite Support** — Network activation and site-specific configuration

---

## 🛒 WooCommerce Integration

On WooCommerce sites:
- Consent checkbox automatically added to checkout form
- Preferences recorded with order data
- View consent details at **WooCommerce → Orders → [Order] → Veribenim Consent** tab

---

## 👨‍💻 Developer Hooks

```php
// Before consent banner loads
add_action('veribenim_before_load', function() { });

// After consent is accepted
add_action('veribenim_after_consent', function($preferences) { });

// Add custom consent categories
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'Custom', 'description' => 'Description'];
    return $categories;
});
```

**REST API Endpoints:**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 Multisite Setup

1. **Network Admin → Settings → Veribenim** — Set global token
2. **Subsite Dashboard → Settings → Veribenim** — Configure own token
3. **Network Admin → Plugins** → **Network Activate**

---

## 🔒 Security Standards

### KVKK Compliance

- ✅ **Article 6:** Consent-based data processing
- ✅ **Article 10:** Data Subject Rights
- ✅ **Article 13:** Transparency Obligation
- ✅ **Article 14:** Data Security

### GDPR Compliance

- ✅ **Article 4:** Designed as Consent Management Platform
- ✅ **Article 7:** Freely Given, Specific, Informed Consent
- ✅ **Article 13:** Information to be Provided to Data Subject
- ✅ **Article 17:** Right to Erasure (Right to be Forgotten)
- ✅ **Article 32:** Security of Processing

### Technical Security

- **Encryption:** TLS 1.3 (AES-256-GCM), Database AES-256
- **API Communication:** HTTPS/TLS 1.3, Bearer Token, CORS, Rate Limiting
- **Audit Trail:** Timestamp, IP address, User-Agent, change log
- **Certifications:** ISO 27001, SOC 2 Type II

### Data Retention

- Required Cookies: Legal obligation (indefinite)
- Analytics: 30 days
- Marketing: 90 days
- Audit Log: 1 year

---

## 📋 Requirements

- **WordPress:** 6.0 or higher
- **PHP:** 8.1 or higher
- **HTTPS:** Required for data security
- **Recommended:** Nginx 1.20+, PostgreSQL 13+, 128MB RAM

---

## ❓ FAQ

**Q: Can I customize Veribenim for my specific needs?**

A: Yes! Customize banner colors, position, and text from the admin panel. Advanced customizations use PHP hooks and filters.

---

**Q: Does Veribenim protect customer data in WooCommerce?**

A: Yes, Veribenim automatically shows consent requirements at WooCommerce checkout and stores preferences with the order.

---

**Q: Does Veribenim affect my SEO?**

A: No. Veribenim loads asynchronously and doesn't negatively impact page speed or Google PageSpeed scores.

---

**Q: Can I use different tokens per site in WordPress Multisite?**

A: Yes, each subsite can have its own token or use the global token from network admin.

---

**Q: What data does Veribenim store?**

A: Only consent preferences, timestamp, and IP address. Sensitive personal data (credit cards, SSN, etc.) is never stored.

---

**Q: Can I test Veribenim before committing?**

A: Yes, we offer a 30-day free trial. Sign up at [app.veribenim.com](https://app.veribenim.com).

---

## 📚 Additional Resources

- [Official Veribenim Documentation](https://docs.veribenim.com)
- [KVKK Guide](https://www.kvk.gov.tr)
- [GDPR Official](https://gdpr.eu)
- [GitHub Repository](https://github.com/pariette/veribenim-wordpress)
- [Veribenim Blog](https://veribenim.com/blog)

---

## 💬 Support

Have questions? Contact us:

- **Email:** support@pariette.com
- **Website:** https://veribenim.com
- **Live Chat:** https://app.veribenim.com/support
- **GitHub Issues:** [Issues Page](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 License

Veribenim WordPress SDK is released under the MIT License. See `LICENSE` file for details.

```
MIT License

Copyright (c) 2024 Pariette

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 🤝 Contributing

Want to help improve Veribenim? Bug reports, feature requests, and pull requests are always welcome.

1. Fork the [GitHub Repository](https://github.com/pariette/veribenim-wordpress)
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

**Secure your data privacy with Veribenim. Eliminate legal risk. Gain customer trust.**

*The World's Most Comprehensive WordPress Data Privacy Solution — Trusted, Complete, Legal.*

---

**Status:** ✅ Active Development | **Last Updated:** April 2, 2026
