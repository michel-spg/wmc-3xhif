---
title: "SSR vs. CSR"
description: "Server-Side Rendering (SSR) vs. Client-Side Rendering (CSR)"
nav_order: 1
layout: default
parent: Nextjs & React
---

<!-- Source --> 
<!-- https://appwrite.io/blog/post/csr-vs-ssr-with-nextjs -->

<!-- ![bg left:50% 80%](../assets/spengergasse_logo_skaliert.png) -->

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# Server-Side Rendering (SSR) vs. Client-Side Rendering (CSR)

Beim **Server-Side Rendering (SSR)** wird die HTML-Seite vollständig auf dem Server generiert und dann an den Browser gesendet. Dies führt zu schnelleren anfänglichen Ladezeiten und einer besseren SEO-Optimierung, da der Inhalt sofort für Suchmaschinen sichtbar ist. Allerdings erhöht sich die Serverlast, und dynamische Interaktionen können komplexer sein.  

Beim **Client-Side Rendering (CSR)** erhält der Browser zunächst minimales HTML und lädt dann JavaScript, um den Inhalt darzustellen. Dies kann die anfängliche Ladezeit verlangsamen, bietet jedoch eine bessere Performance für interaktive Anwendungen nach dem ersten Laden. CSR entlastet den Server, erhöht aber die Rechenlast auf dem Client-Gerät.  

| Feature              | SSR (Server-Side Rendering) | CSR (Client-Side Rendering) |
|----------------------|---------------------------|----------------------------|
| **Rendering location** | Der HTML-Inhalt wird vollständig auf dem Server gerendert und als komplette Seite an den Client gesendet. | Der Browser erhält minimales HTML, und JavaScript rendert den Inhalt auf der Client-Seite. |
| **Initial load time** | Bietet in der Regel schnellere anfängliche Ladezeiten, da der Browser die Seite sofort anzeigen kann. | Kann langsamere anfängliche Ladezeiten haben, da der Browser erst JavaScript laden, parsen und ausführen muss. |
| **SEO Optimization** | SEO-freundlicher, da Suchmaschinen das vollständig gerenderte HTML crawlen können. | Weniger SEO-freundlich, da Suchmaschinen Schwierigkeiten haben könnten, asynchron per JavaScript gerenderten Inhalt zu indexieren. |
| **Resource utilization** | Erhöht die Serverlast, da der Server den Inhalt für jede Anfrage rendern muss. | Entlastet den Server, da das Rendering auf den Client verschoben wird, erhöht aber die Rechenlast des Clients. |
| **User experience** | Bietet eine bessere anfängliche Nutzererfahrung mit schnelleren Ladezeiten. | Kann das Benutzererlebnis in dynamischen Anwendungen mit sanften Übergängen und Interaktionen nach dem ersten Laden verbessern. |
| **Development Complexity** | Kann komplexer sein, insbesondere für hochdynamische Websites, da eine Serverinfrastruktur erforderlich ist. | Einfacher zu implementieren, da das Rendering im Browser erfolgt, aber die Verwaltung des Zustands kann komplizierter werden. |
| **Caching** | Leicht auf Server-Ebene oder über ein CDN zu cachen, da der Inhalt statisch und vorgerendert ist. | Caching-Strategien sind komplexer, da der Inhalt dynamisch gerendert wird, oft sind Service Worker erforderlich. |
| **Data fetching** | Der Server ruft die Daten vor dem Rendern der Seite ab, was die Leistung für das erste Laden verbessern kann. | Die Daten werden clientseitig abgerufen, was die Darstellung des Inhalts verzögern kann. |

## Zusammenfassung  
SSR eignet sich besser für SEO-relevante und performancekritische Anwendungen mit vielen statischen Inhalten, während CSR ideal für interaktive Web-Apps ist, die nach dem Laden viele dynamische Inhalte verwalten. Moderne Frameworks wie Next.js bieten hybride Ansätze, die beide Methoden kombinieren.  
