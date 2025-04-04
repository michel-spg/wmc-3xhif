---
title: "Formularverarbeitung in Next.js"
description: "Client- vs. Server-seitige Ansätze zur Formularverarbeitung in Next.js"
nav_order: 3
layout: default
parent: Nextjs & React
---

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# Formularverarbeitung in Next.js: Client- vs. Server-seitige Ansätze

## Client-seitige Verarbeitung mit `useState` und `fetch`

### Vorteile:
- Einfache Implementierung ohne zusätzliche Bibliotheken.
- Direkte API-Anfragen aus dem Client.
- Einfache Handhabung von Formulardaten.

### *Umsetzung:*
- `useState` verwaltet die Formulardaten und die Zutatenliste.
- `fetch` sendet die Daten an die API.
- Erfolgs- und Fehlermeldungen werden im UI angezeigt.

## Client-seitige Verarbeitung mit `useForm` und `fetch`

### Vorteile:
- `useForm` aus `react-hook-form` bietet eine effiziente und performante Verwaltung von Formularen.
- Client-seitige Validierung, die dem Benutzer sofortiges Feedback gibt.
- Direkte API-Anfragen ohne Server-Interaktion.

### *Umsetzung:*
- `useForm` wird zur Formularsteuerung und Validierung verwendet.
- `handleSubmit` verarbeitet das Absenden der Formulardaten.
- API-Aufruf (`fetch`) sendet die Daten an die API.
- Erfolgs- und Fehlermeldungen werden im UI angezeigt.

---

## Server-seitige Verarbeitung mit `use server` (Server Actions)

### Vorteile:
- Die Formulardaten werden direkt serverseitig verarbeitet, wodurch sensible Daten nicht im Client gespeichert werden müssen.
- Keine unnötigen API-Anfragen aus dem Client – die Datenverarbeitung erfolgt vollständig auf dem Server.
- Einfachere Handhabung von Datenbankinteraktionen.

### *Umsetzung:*
- Eine Server Action (zB `submitRecipe.ts`) übernimmt die Formularverarbeitung.
- `FormData` wird verwendet, um die Daten an den Server zu übergeben.
- `action={submitRecipe}` ersetzt die `onSubmit`-Funktion im TSX.
- Erfolgreiche Verarbeitung oder Fehlerbehandlung erfolgt direkt in der Server Action.
- Das UI zeigt eine Bestätigungsmeldung nach erfolgreichem Absenden.

---
