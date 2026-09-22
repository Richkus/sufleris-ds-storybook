# Mokesčių Sufleris DS — Admin

Statinis "Design System admin" puslapis, sukurtas naudojant kliento realų
produkcinį stack'ą (Twig + SCSS/Bootstrap 5 per Webpack Encore + Alpine.js),
kad būtų lengvai integruojamas/perpanaudojamas realiame produkte.

Šis repo yra **galutinė, IT komandai skirta versija** — vienas fiksuotas
shell/layout variantas, be eksperimentinių alternatyvų. Eksperimentavimo
istorija (alternatyvūs layout'ai, prototipiniai puslapiai) liko atskirame
repo (`sufleris-ds-admin`) ir čia sąmoningai nekopijuota.

## Struktūra

- **Twig** šablonai (`templates/`) kompiliuojami į statinį HTML per
  `scripts/render-twig.js` (naudojant `twing`, Node Twig implementaciją —
  šablonai rašyti taip, kad su minimaliais pakeitimais veiktų ir realiame
  Symfony/Twig backend'e).
- **SCSS + Bootstrap 5** stiliai (`assets/styles/`), sudėliojami per Webpack
  Encore. Visi spalvų/tarpų/tipografijos tokenai — `assets/styles/_variables.scss`
  (raw paletė) ir `assets/styles/_theme.scss` (semantiniai CSS custom
  properties, `--ds-*`, kuriuos naudoja komponentai).
- **Alpine.js** interaktyvumui (dropdown'ai, sidebar accordion, DialKit
  valdikis) — ne jQuery, ne Bootstrap JS bundle.
- Sugeneruotas rezultatas atsiduria `public/` kataloge (negrafuojamas į git).

## Paleidimas

```bash
npm install
```

### Dev (vienkartinis build)

```bash
npm run dev
```

### Watch (automatinis perkompiliavimas keičiant failus)

```bash
npm run watch
```

### Production build

```bash
npm run build
```

Kiekviena komanda pirmiausia sugeneruoja HTML iš Twig šablonų
(`npm run render`), tada paleidžia Webpack Encore SCSS/JS kompiliavimui.
Rezultatas: `public/index.html` + kiti puslapiai + `public/build/app.css` /
`public/build/app.js`.

## DialKit valdiklis

Apatiniame dešiniajame kampe esantis 🪄 mygtukas atidaro live valdymo
skydelį — šrifto (sans + serifinio) keitimą ir kodo pavyzdžių rodymo
perjungiklį. Tai vidinis dev-tools elementas prototipavimui, ne realaus
produkto UI dalis.
