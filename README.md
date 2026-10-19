# KickTime 2026 – Info- & Supportseite

Statische Seite zu **KickTime 2026**, dem persönlichen Begleiter zur FIFA WM 2026:
Rückblick auf die App, Installationsanleitung, häufige Fragen, Kontaktformular sowie
Impressum und Datenschutzerklärung.

## Aufbau

- `index.html` – Startseite (App, Installieren, Fragen, Support)
- `impressum.html`, `datenschutz.html` – Rechtstexte
- `assets/css/style.css` – komplettes Styling (Dark/Light über `prefers-color-scheme`)
- `assets/js/main.js` – Menü, Einblenden beim Scrollen, Kontaktformular, Weiterleitung alter Anker (`#impressum`, `#datenschutz`)
- `assets/fonts/` – selbst gehostete Schriften (Space Grotesk, Inter), keine Google-Fonts-Anfragen
- `_headers` – Sicherheits-Header für Cloudflare Pages (CSP)

Kein Build-Schritt, keine Bibliotheken, kein Tracking.

## Lokal ansehen

```sh
python3 -m http.server 8080
```

Dann `http://localhost:8080` öffnen.

## Hinweise

- Das Kontaktformular sendet an Formspree (`https://formspree.io/f/mpqnnabg`).
- Die CSP in `_headers` erlaubt das kleine Inline-Skript im `<head>` per SHA-256-Hash.
  Wird das Skript geändert, muss der Hash neu berechnet werden:
  `printf '%s' '<inhalt>' | openssl dgst -sha256 -binary | base64`
- Keine Inline-`style`-Attribute verwenden – die CSP blockiert sie.
