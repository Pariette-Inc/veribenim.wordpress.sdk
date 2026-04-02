# Veribenim WordPress SDK

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**La solution WordPress la plus complète pour la protection des données | Conforme KVKK & GDPR**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Compliant-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## Qu'est-ce que Veribenim?

Veribenim est **la plateforme la plus complète au monde de gestion du consentement et de la confidentialité des données**, développée par Pariette. Intégrez-la facilement sur vos sites WordPress pour assurer une conformité juridique complète concernant la collecte et le traitement des données personnelles des visiteurs.

---

## 🎯 Pourquoi Veribenim?

### 1. Solution KVKK la plus complète
Veribenim est conçue pour répondre à toutes les exigences fixées par l'Autorité turque de protection des données (KVKK). Conformément à l'article 6, les données basées sur le consentement sont collectées et gérées dans le cadre d'un consentement explicite. Le système d'audit trail enregistre chaque consentement.

### 2. Architecture entièrement conforme au GDPR
Pour les sites opérant en Europe, l'article 7 du GDPR (Preuve du consentement) et l'article 13 (Obligations de transparence) sont entièrement satisfaits. La bannière de consentement multilingue répond aux exigences du GDPR.

### 3. Injection de script automatique
Aucun codage requis après l'installation. Veribenim injecte automatiquement le bundle JavaScript dans les balises WordPress `<head>`. La communication cryptée SSL/TLS est standard.

### 4. Architecture conviviale pour les développeurs
Hooks PHP, points de terminaison API REST et système de hooks WordPress pour les intégrations WordPress sans tête et personnalisées. Les codes courts et les blocs Gutenberg permettent aux utilisateurs non techniques de prendre le contrôle.

### 5. Support Multisite & Enterprise
Support de jeton indépendant pour chaque sous-site dans votre réseau WordPress Multisite. Configuration globale ou spécifique au site possible.

### 6. Audit et rapport en temps réel
Toutes les décisions de consentement sont enregistrées dans la base de données. Le panneau d'administration affiche avec la date et l'adresse IP quelles catégories ont été acceptées/refusées.

### Comparaison : Veribenim vs. autres solutions

| Fonctionnalité | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **Conforme KVKK** | ✅ | ❌ | ✅ | ❌ |
| **Conforme GDPR** | ✅ | ✅ | ✅ | ✅ |
| **Support français natif** | ✅ | ⚠️ Limité | ⚠️ Limité | ✅ |
| **WordPress natif** | ✅ | ✅ | ⚠️ Script | ✅ |
| **WooCommerce intégré** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Support multisite** | ✅ | ❌ | ❌ | ❌ |
| **Hooks PHP** | ✅ | ❌ | ❌ | ⚠️ |
| **Équipe française** | ✅ | ❌ | ❌ | ⚠️ |

---

## 📋 Table des matières

1. [Installation](#comment-installer)
2. [Démarrage rapide](#démarrage-rapide)
3. [Fonctionnalités](#fonctionnalités)
4. [Intégration WooCommerce](#intégration-woocommerce)
5. [Hooks développeur](#hooks-développeur)
6. [Configuration Multisite](#configuration-multisite)
7. [Normes de sécurité](#normes-de-sécurité)
8. [Exigences](#exigences)

---

## 🚀 Comment installer?

### Méthode 1 : Depuis le panneau d'administration WordPress

1. Connectez-vous au tableau de bord WordPress
2. Accédez à **Extensions → Ajouter une extension**
3. Recherchez **"Veribenim"**
4. Cliquez sur **Installer → Activer**

### Méthode 2 : Composer

```bash
composer require veribenim/wordpress
```

Activez ensuite l'extension depuis le tableau de bord WordPress.

### Méthode 3 : Installation manuelle

1. Téléchargez `veribenim-wordpress.zip` depuis la [page des versions](https://github.com/pariette/veribenim-wordpress/releases)
2. Téléchargez-le vers `wp-content/plugins/`
3. Activez-le depuis le tableau de bord

### Configuration après installation

1. Accédez à **Paramètres → Veribenim**
2. Copiez votre jeton de site depuis [app.veribenim.com](https://app.veribenim.com) → Votre site → Intégration
3. Collez le jeton dans le champ **Jeton du site Veribenim**
4. Sélectionnez votre langue préférée (Türkçe, English, Deutsch, Français, Español, Български, العربية)
5. Cliquez sur **Enregistrer**

✅ La bannière Veribenim s'affichera maintenant sur tous vos sites.

---

## ⚡ Démarrage rapide

```php
// Quand le consentement est accepté
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('Consentement accepté: ' . json_encode($preferences));
});

// Quand le consentement est refusé
add_action('veribenim_declined', function() {
    error_log('Consentement refusé');
});

// Ajouter des métadonnées au consentement
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 Fonctionnalités

- **Injection de script automatique** — Bundle JavaScript automatiquement injecté dans la section `<head>`
- **Panneau de paramètres d'administration** — Jeton, langue et personnalisation de la bannière en une page
- **Conception indépendante du thème** — Fonctionne avec tous les thèmes WordPress
- **Compatible WooCommerce** — Consentement au paiement, stocké avec les détails de la commande
- **Mises à jour basées sur AJAX** — Mettre à jour les préférences sans rechargement de page
- **Support API REST** — Intégration WordPress sans tête
- **Code court & Bloc Gutenberg** — Support du code court `[veribenim_consent]` et de l'éditeur de blocs
- **Compatible avec les plugins de cache** — Fonctionne avec WP Rocket, W3 Total Cache, LiteSpeed Cache
- **Support multisite** — Activation réseau et configuration spécifique au site

---

## 🛒 Intégration WooCommerce

Sur les sites WooCommerce :
- Case à cocher de consentement automatiquement ajoutée au paiement
- Préférences enregistrées avec les données de commande
- Afficher les détails du consentement à **WooCommerce → Commandes → [Commande] → Consentement Veribenim**

---

## 👨‍💻 Hooks développeur

```php
// Avant le chargement de la bannière de consentement
add_action('veribenim_before_load', function() { });

// Après l'acceptation du consentement
add_action('veribenim_after_consent', function($preferences) { });

// Ajouter des catégories de consentement personnalisées
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'Personnalisé', 'description' => 'Description'];
    return $categories;
});
```

**Points de terminaison API REST :**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 Configuration Multisite

1. **Admin réseau → Paramètres → Veribenim** — Définir le jeton global
2. **Tableau de bord du sous-site → Paramètres → Veribenim** — Configurer le jeton personnel
3. **Admin réseau → Extensions** → **Activer sur le réseau**

---

## 🔒 Normes de sécurité

### Conformité KVKK

- ✅ **Article 6 :** Traitement basé sur le consentement
- ✅ **Article 10 :** Droits de la personne concernée
- ✅ **Article 13 :** Obligation de transparence
- ✅ **Article 14 :** Sécurité des données

### Conformité GDPR

- ✅ **Article 4 :** Conçu en tant que plateforme de gestion du consentement
- ✅ **Article 7 :** Consentement libre, spécifique et éclairé
- ✅ **Article 13 :** Informations pour la personne concernée
- ✅ **Article 17 :** Droit à l'oubli (Droit d'effacement)
- ✅ **Article 32 :** Sécurité du traitement

### Sécurité technique

- **Chiffrement :** TLS 1.3 (AES-256-GCM), base de données AES-256
- **Communication API :** HTTPS/TLS 1.3, jeton Bearer, CORS, limitation de débit
- **Audit Trail :** Horodatage, adresse IP, User-Agent, journal des modifications
- **Certifications :** ISO 27001, SOC 2 Type II

### Conservation des données

- Cookies requis : Obligation légale (indéfini)
- Analytics : 30 jours
- Marketing : 90 jours
- Journal d'audit : 1 an

---

## 📋 Exigences

- **WordPress :** 6.0 ou supérieur
- **PHP :** 8.1 ou supérieur
- **HTTPS :** Requis pour la sécurité des données
- **Recommandé :** Nginx 1.20+, PostgreSQL 13+, 128MB RAM

---

## ❓ FAQ

**Q : Puis-je personnaliser Veribenim selon mes besoins?**

R : Oui ! Personnalisez les couleurs, la position et le texte de la bannière depuis le panneau d'administration. Les personnalisations avancées utilisent les hooks et filtres PHP.

---

**Q : Veribenim protège-t-il les données des clients dans WooCommerce?**

R : Oui, Veribenim affiche automatiquement les exigences de consentement lors du paiement WooCommerce et stocke les préférences avec la commande.

---

**Q : Veribenim affecte-t-il mon référencement?**

R : Non. Veribenim se charge de manière asynchrone et n'affecte pas négativement la vitesse de page ou les scores Google PageSpeed.

---

**Q : Puis-je utiliser des jetons différents par site dans WordPress Multisite?**

R : Oui, chaque sous-site peut avoir son propre jeton ou utiliser le jeton global de l'administrateur réseau.

---

**Q : Quelles données Veribenim stocke-t-il?**

R : Seules les préférences de consentement, l'horodatage et l'adresse IP. Les données personnelles sensibles (cartes de crédit, numéro de sécurité sociale, etc.) ne sont jamais stockées.

---

**Q : Puis-je tester Veribenim avant de me engager?**

R : Oui, nous offrons un essai gratuit de 30 jours. Inscrivez-vous sur [app.veribenim.com](https://app.veribenim.com).

---

## 📚 Ressources supplémentaires

- [Documentation officielle de Veribenim](https://docs.veribenim.com)
- [Guide KVKK](https://www.kvk.gov.tr)
- [GDPR officiel](https://gdpr.eu)
- [Référentiel GitHub](https://github.com/pariette/veribenim-wordpress)
- [Blog Veribenim](https://veribenim.com/blog)

---

## 💬 Assistance

Avez-vous des questions? Contactez-nous :

- **Email :** support@pariette.com
- **Site Web :** https://veribenim.com
- **Chat en direct :** https://app.veribenim.com/support
- **Problèmes GitHub :** [Page des problèmes](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 Licence

Veribenim WordPress SDK est publié sous la licence MIT. Voir le fichier `LICENSE` pour plus de détails.

---

## 🤝 Contribuer

Vous voulez aider à améliorer Veribenim? Les rapports de bogues, les demandes de fonctionnalités et les demandes d'extraction sont toujours les bienvenues.

1. Forkez le [référentiel GitHub](https://github.com/pariette/veribenim-wordpress)
2. Créez une branche de fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Validez vos modifications (`git commit -m 'Add AmazingFeature'`)
4. Poussez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une demande d'extraction

---

**Sécurisez la confidentialité de vos données avec Veribenim. Éliminez les risques juridiques. Gagnez la confiance des clients.**

*La solution WordPress la plus complète au monde pour la protection des données — Fiable, Complète, Conforme.*

---

**Statut :** ✅ Développement actif | **Dernière mise à jour :** 2 avril 2026
