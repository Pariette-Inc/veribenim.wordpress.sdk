# Veribenim WordPress SDK

![Veribenim Banner](https://veribenim.com/assets/banner.png)

**La solución más completa de privacidad de datos de WordPress | Conforme KVKK & GDPR**

[![Latest Version](https://img.shields.io/packagist/v/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![WordPress Version](https://img.shields.io/badge/WordPress-6.0%2B-blue)](https://wordpress.org)
[![PHP Version](https://img.shields.io/badge/PHP-8.1%2B-purple)](https://www.php.net)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Downloads](https://img.shields.io/packagist/dt/veribenim/wordpress)](https://packagist.org/packages/veribenim/wordpress)
[![KVKK Compliant](https://img.shields.io/badge/KVKK-Compliant-red)](https://www.kvk.gov.tr)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-blue)](https://gdpr.eu)

---

## ¿Qué es Veribenim?

Veribenim es **la plataforma más completa del mundo para gestión de consentimiento y privacidad de datos**, desarrollada por Pariette. Intégrelo fácilmente en sus sitios WordPress para garantizar el cumplimiento legal completo con respecto a la recopilación y el procesamiento de datos personales de los visitantes.

---

## 🎯 ¿Por qué Veribenim?

### 1. Solución KVKK más completa
Veribenim está diseñado para cumplir con todos los requisitos establecidos por la Autoridad Turca de Protección de Datos (KVKK). Según el Artículo 6, los datos basados en consentimiento se recopilan y administran dentro del alcance del consentimiento explícito. El sistema de auditoría registra cada consentimiento.

### 2. Arquitectura totalmente conforme con GDPR
Para sitios que operan en Europa, el Artículo 7 del GDPR (Prueba de consentimiento) y el Artículo 13 (Obligación de transparencia) están completamente satisfechos. El banner de consentimiento multilingüe cumple con los requisitos del GDPR.

### 3. Inyección automática de scripts
No se requiere codificación después de la instalación. Veribenim inyecta automáticamente el paquete de JavaScript en las etiquetas de WordPress `<head>`. La comunicación cifrada SSL/TLS es estándar.

### 4. Arquitectura compatible con desarrolladores
Hooks PHP, puntos finales de API REST y sistema de hooks de WordPress para integraciones de WordPress sin encabezado y personalizadas. Códigos cortos y bloques de Gutenberg permiten a usuarios no técnicos tomar el control.

### 5. Soporte Multisite & Enterprise
Soporte de token independiente para cada subsite en su red WordPress Multisite. Configuración global o específica del sitio posible.

### 6. Auditoría e informes en tiempo real
Todas las decisiones de consentimiento se registran en la base de datos. El panel de administración muestra con fecha y dirección IP qué categorías fueron aceptadas/rechazadas.

### Comparación: Veribenim vs. otras soluciones

| Característica | Veribenim | CookieBot | OneTrust | Cookyes |
|---------|-----------|-----------|----------|---------|
| **Conforme KVKK** | ✅ | ❌ | ✅ | ❌ |
| **Conforme GDPR** | ✅ | ✅ | ✅ | ✅ |
| **Soporte español nativo** | ✅ | ⚠️ Limitado | ⚠️ Limitado | ✅ |
| **WordPress nativo** | ✅ | ✅ | ⚠️ Script | ✅ |
| **WooCommerce integrado** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Soporte multisitio** | ✅ | ❌ | ❌ | ❌ |
| **Hooks PHP** | ✅ | ❌ | ❌ | ⚠️ |
| **Equipo español** | ✅ | ❌ | ❌ | ⚠️ |

---

## 📋 Tabla de contenidos

1. [Instalación](#cómo-instalar)
2. [Inicio rápido](#inicio-rápido)
3. [Características](#características)
4. [Integración WooCommerce](#integración-woocommerce)
5. [Hooks para desarrolladores](#hooks-para-desarrolladores)
6. [Configuración Multisite](#configuración-multisite)
7. [Estándares de seguridad](#estándares-de-seguridad)
8. [Requisitos](#requisitos)

---

## 🚀 ¿Cómo instalar?

### Método 1: Desde el panel de administración de WordPress

1. Inicie sesión en el panel de control de WordPress
2. Vaya a **Complementos → Añadir nuevo**
3. Busque **"Veribenim"**
4. Haga clic en **Instalar → Activar**

### Método 2: Composer

```bash
composer require veribenim/wordpress
```

Luego active el complemento desde el panel de control de WordPress.

### Método 3: Instalación manual

1. Descargue `veribenim-wordpress.zip` desde la [página de versiones](https://github.com/pariette/veribenim-wordpress/releases)
2. Cárguelo en `wp-content/plugins/`
3. Actívelo desde el panel de control

### Configuración después de la instalación

1. Vaya a **Ajustes → Veribenim**
2. Copie su token de sitio desde [app.veribenim.com](https://app.veribenim.com) → Su sitio → Integración
3. Pegue el token en el campo **Token del sitio Veribenim**
4. Seleccione su idioma preferido (Türkçe, English, Deutsch, Français, Español, Български, العربية)
5. Haga clic en **Guardar**

✅ El banner de Veribenim ahora aparecerá en todos sus sitios.

---

## ⚡ Inicio rápido

```php
// Cuando se acepta el consentimiento
add_action('veribenim_consent_accepted', function($preferences) {
    // $preferences = ['necessary'=>true, 'analytics'=>true, 'marketing'=>false]
    error_log('Consentimiento aceptado: ' . json_encode($preferences));
});

// Cuando se rechaza el consentimiento
add_action('veribenim_declined', function() {
    error_log('Consentimiento rechazado');
});

// Agregar metadatos al consentimiento
add_filter('veribenim_consent_metadata', function($metadata) {
    $metadata['user_role'] = get_current_user()->roles[0] ?? 'guest';
    return $metadata;
});
```

---

## 🎨 Características

- **Inyección automática de scripts** — Paquete de JavaScript inyectado automáticamente en la sección `<head>`
- **Panel de configuración de administrador** — Token, idioma y personalización de banner en una página
- **Diseño independiente del tema** — Funciona con todos los temas de WordPress
- **Compatible con WooCommerce** — Consentimiento en el pago, almacenado con detalles del pedido
- **Actualizaciones basadas en AJAX** — Actualizar preferencias sin recarga de página
- **Soporte de API REST** — Integración de WordPress sin encabezado
- **Código corto y bloque Gutenberg** — Soporte de código corto `[veribenim_consent]` y editor de bloques
- **Compatible con plugins de caché** — Funciona con WP Rocket, W3 Total Cache, LiteSpeed Cache
- **Soporte Multisite** — Activación de red y configuración específica del sitio

---

## 🛒 Integración WooCommerce

En sitios WooCommerce:
- Casilla de consentimiento agregada automáticamente al pago
- Preferencias guardadas con datos de pedido
- Ver detalles de consentimiento en **WooCommerce → Pedidos → [Pedido] → Consentimiento Veribenim**

---

## 👨‍💻 Hooks para desarrolladores

```php
// Antes de cargar el banner de consentimiento
add_action('veribenim_before_load', function() { });

// Después de aceptar el consentimiento
add_action('veribenim_after_consent', function($preferences) { });

// Agregar categorías de consentimiento personalizadas
add_filter('veribenim_consent_categories', function($categories) {
    $categories['custom'] = ['label' => 'Personalizado', 'description' => 'Descripción'];
    return $categories;
});
```

**Puntos finales de API REST:**
```bash
GET /wp-json/veribenim/v1/consent/{user_id}
POST /wp-json/veribenim/v1/consent
```

---

## 🌐 Configuración Multisite

1. **Admin de red → Ajustes → Veribenim** — Establecer token global
2. **Panel de control del subsitio → Ajustes → Veribenim** — Configurar token propio
3. **Admin de red → Complementos** → **Activar en la red**

---

## 🔒 Estándares de seguridad

### Conformidad KVKK

- ✅ **Artículo 6 :** Procesamiento basado en consentimiento
- ✅ **Artículo 10 :** Derechos del sujeto de datos
- ✅ **Artículo 13 :** Obligación de transparencia
- ✅ **Artículo 14 :** Seguridad de datos

### Conformidad GDPR

- ✅ **Artículo 4 :** Diseñado como plataforma de gestión del consentimiento
- ✅ **Artículo 7 :** Consentimiento libre, específico e informado
- ✅ **Artículo 13 :** Información para el sujeto de datos
- ✅ **Artículo 17 :** Derecho al olvido (Derecho a la supresión)
- ✅ **Artículo 32 :** Seguridad del procesamiento

### Seguridad técnica

- **Encriptación :** TLS 1.3 (AES-256-GCM), base de datos AES-256
- **Comunicación API :** HTTPS/TLS 1.3, token Bearer, CORS, limitación de velocidad
- **Auditoría :** Marca de tiempo, dirección IP, User-Agent, registro de cambios
- **Certificaciones :** ISO 27001, SOC 2 Type II

### Retención de datos

- Cookies requeridas: Obligación legal (indefinido)
- Analytics: 30 días
- Marketing: 90 días
- Registro de auditoría: 1 año

---

## 📋 Requisitos

- **WordPress :** 6.0 o superior
- **PHP :** 8.1 o superior
- **HTTPS :** Requerido para la seguridad de datos
- **Recomendado :** Nginx 1.20+, PostgreSQL 13+, 128MB RAM

---

## ❓ Preguntas frecuentes

**P: ¿Puedo personalizar Veribenim según mis necesidades?**

R: ¡Sí! Personalice los colores, la posición y el texto del banner desde el panel de administración. Las personalizaciones avanzadas utilizan hooks y filtros PHP.

---

**P: ¿Veribenim protege los datos de los clientes en WooCommerce?**

R: Sí, Veribenim muestra automáticamente los requisitos de consentimiento en el pago de WooCommerce y almacena las preferencias con el pedido.

---

**P: ¿Afecta Veribenim a mi SEO?**

R: No. Veribenim se carga de forma asincrónica y no afecta negativamente a la velocidad de la página ni a las puntuaciones de Google PageSpeed.

---

**P: ¿Puedo usar diferentes tokens por sitio en WordPress Multisite?**

R: Sí, cada subsitio puede tener su propio token o usar el token global del administrador de red.

---

**P: ¿Qué datos almacena Veribenim?**

R: Solo preferencias de consentimiento, marca de tiempo y dirección IP. Los datos personales sensibles (tarjetas de crédito, número de seguro social, etc.) nunca se almacenan.

---

**P: ¿Puedo probar Veribenim antes de comprometerse?**

R: Sí, ofrecemos una prueba gratuita de 30 días. Regístrese en [app.veribenim.com](https://app.veribenim.com).

---

## 📚 Recursos adicionales

- [Documentación oficial de Veribenim](https://docs.veribenim.com)
- [Guía KVKK](https://www.kvk.gov.tr)
- [GDPR oficial](https://gdpr.eu)
- [Repositorio de GitHub](https://github.com/pariette/veribenim-wordpress)
- [Blog de Veribenim](https://veribenim.com/blog)

---

## 💬 Soporte

¿Tiene preguntas? Contáctenos:

- **Correo electrónico :** support@pariette.com
- **Sitio web :** https://veribenim.com
- **Chat en vivo :** https://app.veribenim.com/support
- **Problemas de GitHub :** [Página de problemas](https://github.com/pariette/veribenim-wordpress/issues)

---

## 📄 Licencia

Veribenim WordPress SDK se publica bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.

---

## 🤝 Contribuir

¿Quiere ayudar a mejorar Veribenim? Los reportes de errores, solicitudes de características y solicitudes de extracción siempre son bienvenidos.

1. Bifurque el [repositorio de GitHub](https://github.com/pariette/veribenim-wordpress)
2. Cree una rama de características (`git checkout -b feature/AmazingFeature`)
3. Confirme sus cambios (`git commit -m 'Add AmazingFeature'`)
4. Envíe a la rama (`git push origin feature/AmazingFeature`)
5. Abra una solicitud de extracción

---

**Asegure la privacidad de sus datos con Veribenim. Elimine el riesgo legal. Gane la confianza del cliente.**

*La solución de privacidad de datos de WordPress más completa del mundo — Confiable, Completa, Conforme.*

---

**Estado:** ✅ Desarrollo activo | **Última actualización:** 2 de abril de 2026
