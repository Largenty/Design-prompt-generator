<div align="center">

# DESIGN.MD / Generator

**Forge des prompts Claude Design forts & personnels.**

Un design fort n'existe pas par accident. Il naît d'une thèse claire, d'un parti pris assumé, d'une signature mémorable.
Cet outil force ce travail amont avant l'écriture du prompt.

[![License: MIT](https://img.shields.io/badge/License-MIT-E8784A.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Live Demo](https://img.shields.io/badge/demo-vercel-0A0907?style=flat-square&logo=vercel)](https://design-prompt-generator-tau.vercel.app/)
[![No Framework](https://img.shields.io/badge/framework-vanilla-0A0907?style=flat-square)](#tech-stack)
[![Single File](https://img.shields.io/badge/distribution-single--HTML-0A0907?style=flat-square)](#installation)
[![getdesign.md](https://img.shields.io/badge/anchors-getdesign.md-E8784A?style=flat-square)](https://getdesign.md)

[**🚀 Live Demo**](https://design-prompt-generator-tau.vercel.app/) · [Installation](#installation) · [Philosophie](#philosophie) · [Anchors](#les-anchors-disponibles) · [Roadmap](#roadmap)

</div>

---

> **TL;DR (en)** — A single-file generator for crafting opinionated Claude Design prompts. Pre-flight strategic questions force you to define your thesis before writing the brief. A dual-mode toggle system lets you either impose execution decisions (fonts, palette, anchor, etc.) manually, or let Claude propose 2 options at validation time. Built brutalist-dark with Instrument Serif + Geist + JetBrains Mono. Auto-saves to localStorage. No framework, no tracker, no cookie, no dependency.

---

## Sommaire

- [Pourquoi cet outil](#pourquoi-cet-outil)
- [Demo](#demo)
- [Installation](#installation)
- [Philosophie](#philosophie)
- [Les 7 questions pre-flight](#les-7-questions-pre-flight)
- [Le dual mode MANUEL / AUTO](#le-dual-mode-manuel--auto)
- [Anatomie du prompt généré](#anatomie-du-prompt-généré)
- [Les anchors disponibles](#les-anchors-disponibles)
- [Tech stack](#tech-stack)
- [Personnalisation & fork](#personnalisation--fork)
- [Roadmap](#roadmap)
- [Crédits](#crédits)
- [License](#license)

---

## Pourquoi cet outil

Quand on demande à Claude (ou à n'importe quel LLM) de produire un design, le rendu par défaut est mou. Du SaaS gris avec gradient violet. Une typo Inter / Roboto sans relief. Des photos stock corporate. Le plus petit dénominateur commun de tout ce qu'il a vu pendant son training.

Ce n'est pas un problème de capacité — c'est un problème de **brief**. Un design fort exige :

1. **Une thèse claire** — pas "moderne élégant pro" mais une position assumée
2. **Un ancrage culturel** — un design system existant qui sert de grammaire
3. **Une liste explicite d'anti-patterns** — ce que la concurrence fait et qu'on refuse de reproduire
4. **Une signature visuelle unique** — l'idée graphique qu'on retient quand l'onglet est fermé
5. **Des tokens exposés** — pour le handoff vers un vrai projet Next.js / Tailwind
6. **Une validation amont** — Claude propose en 5 lignes avant de produire 7 pages

Cet outil structure ces 6 leviers en un formulaire guidé, et génère un prompt markdown prêt à coller dans une nouvelle conversation Claude.

> *Sans thèse, pas de design. L'outil refuse de te laisser sauter cette étape.*

---

## Demo

🚀 **Live demo** → **[design-prompt-generator-tau.vercel.app](https://design-prompt-generator-tau.vercel.app/)**

Hébergé en static sur Vercel · aucun backend, aucun cookie, aucun tracker.

Pour le faire tourner localement ou le déployer ailleurs, voir [Installation](#installation) ci-dessous.

---

## Installation

L'outil tient dans **un seul fichier HTML autonome** (`index.html`). Aucune dépendance, aucun build, aucun serveur requis.

### Option 1 — En local

```bash
git clone https://github.com/[ton-username]/design-prompt-generator.git
cd design-prompt-generator
open index.html       # macOS
# ou
xdg-open index.html   # Linux
# ou
start index.html      # Windows
```

### Option 2 — Déploiement statique

Drag-and-drop le fichier `index.html` sur :

- [Vercel](https://vercel.com/new) — `vercel deploy` (utilisé pour la demo)
- [Netlify Drop](https://app.netlify.com/drop) — glisse le fichier
- [Cloudflare Pages](https://pages.cloudflare.com/) — connecte ton repo
- [GitHub Pages](https://pages.github.com/) — active Pages sur le repo

Le fichier charge ses 3 fonts depuis Google Fonts. Pas de backend, pas d'API, pas de tracker.

### Option 3 — Embed dans une page existante

Le HTML est autonome. Tu peux l'iframer ou copier la balise `<style>` + le `<body>` dans une page existante. Les styles sont scopés sous des sélecteurs spécifiques.

---

## Philosophie

L'outil est construit autour de **2 principes UX**.

### 1. La pre-flight avant la rédaction

Avant de remplir le formulaire, l'onglet **Comprendre** documente les 6 leviers à actionner et te demande de répondre à 7 questions stratégiques. Si tu ne peux pas y répondre, tu n'écris pas le prompt — tu retournes réfléchir à la thèse.

### 2. Le dual mode manuel / auto

Toutes les questions ne sont pas équivalentes. Les questions **stratégiques** (audience, signature, objet du monde réel, crime concurrent) sont ta thèse — elles ne sont pas négociables par Claude. Les questions d'**exécution** (anchor, polices, palette, mots-clés, catégories d'images) peuvent soit être imposées par toi, soit déléguées à Claude qui proposera 2 options lors du cadrage.

> *Pas de hex codes en tête à 16h ? Bascule la palette en AUTO. Tu décides à la validation, pas à la rédaction.*

---

## Les 7 questions pre-flight

Ces questions sont **toujours user-driven**. C'est ta thèse, elle définit le cap du projet.

| # | Question | Pourquoi c'est crucial |
|---|----------|------------------------|
| 1 | **Le projet en une phrase de 12 mots max** | Si tu n'y arrives pas, ta thèse est trouble |
| 2 | **L'audience cible et ce qu'elle valorise** | Définit la palette émotionnelle |
| 3 | **L'objet du monde réel auquel le site doit ressembler** | L'ancrage culturel — sans lui, design SaaS générique |
| 4 | **La signature visuelle unique** | L'idée graphique qu'on retient quand l'onglet est fermé |
| 5 | **Le crime esthétique #1 de la concurrence** | Définit explicitement ce qu'on refuse |
| 6 | **L'anchor design system** | La grammaire visuelle de référence (auto possible) |
| 7 | **Le nom de la direction créative** | "Phosphor Editorial", "Auric Editorial"... un nom = une thèse |

---

## Le dual mode MANUEL / AUTO

5 sous-sections sont toggleables entre **MANUEL** (tu imposes) et **AUTO** (Claude propose au cadrage) :

| Sous-section | Étape | Cas d'usage AUTO |
|--------------|-------|------------------|
| 🅰️ **Anchor design system** | 01 | Tu n'as pas exploré getdesign.md récemment |
| 🅰️ **Polices** | 02 | Tu n'as pas de couple display+body en tête |
| 🎨 **Palette** | 02 | Tu n'as pas de charte couleur imposée |
| 💬 **Mots-clés artistiques** | 03 | Tu fais confiance à la direction pour les dériver |
| 🖼️ **Images** | 03 | Tu veux les catégories cohérentes avec ton "objet du monde réel" |

Les **contraintes** (couleurs interdites ⛔ / clichés visuels interdits ⛔) restent **toujours visibles et appliquées dans les deux modes**. Un garde-fou est un garde-fou, qu'on choisisse ou qu'on délègue.

### Cas d'usage limites

- **100% MANUEL** → Reproduction d'un design existant, charte client stricte
- **100% AUTO** (sauf 5 questions stratégiques) → Tu as la thèse mais pas l'exécution. Claude propose tout au cadrage, tu valides en 2-3 minutes, puis il produit les pages.

---

## Anatomie du prompt généré

Le prompt markdown produit suit cette structure invariante :

```markdown
# Brief design — [Nom du projet]

## Contexte
## Objectif
## Analyse de la concurrence — patterns à NE PAS reproduire
## Direction créative — "[Nom de la direction]"
  - Anchor design system (manuel ou auto)
  - Typographie (manuel ou auto)
  - Surfaces & palette (manuel ou auto)
  - Espacements
  - Composants
## Signature visuelle mémorable
## Pages à concevoir
## Direction artistique — mots-clés (manuel ou auto)
## Images — OBLIGATOIRE (manuel ou auto)
## Livrables techniques (CSS variables :root)
## Hors-scope (ne PAS produire)
## Méthode de travail (cadrage 5 lignes avant production)
```

Le prompt typique fait entre **3 500 et 6 000 caractères** selon les choix manuel / auto.

---

## Les anchors disponibles

L'outil propose 25 anchors présélectionnés depuis [getdesign.md](https://getdesign.md), organisés par univers visuel :

<details>
<summary><strong>Editorial / Warm</strong></summary>

- **Notion** — warm minimalism, serif headings, soft surfaces
- **Claude** — warm terracotta accent, clean editorial layout
- **Mastercard** — warm cream canvas, editorial warmth
- **Starbucks** — warm cream canvas, four-tier green system

</details>

<details>
<summary><strong>Luxury / Dramatic Dark</strong></summary>

- **Lamborghini** — true black, gold accents, dramatic uppercase
- **BMW M** — pure black canvas, M tricolor stripes
- **Bugatti** — cinema-black, monochrome austerity
- **Ferrari** — chiaroscuro editorial, Ferrari Red

</details>

<details>
<summary><strong>Tech / Dev Tool</strong></summary>

- **Vercel** — black and white precision, Geist font
- **Stripe** — signature purple gradients, weight-300 elegance
- **Linear** — ultra-minimal, precise, purple accent
- **Supabase** — dark emerald theme, code-first
- **Raycast** — sleek dark chrome, gradient accents
- **Cursor** — sleek dark AI interface

</details>

<details>
<summary><strong>Editorial / Magazine</strong></summary>

- **WIRED** — paper-white broadsheet, custom serif, ink-blue links
- **The Verge** — acid-mint and ultraviolet, Manuka display

</details>

<details>
<summary><strong>Cinematic / Minimal Radical</strong></summary>

- **Tesla** — radical subtraction, full-viewport photography
- **Apple** — premium white space, SF Pro, cinematic
- **SpaceX** — stark black and white, full-bleed imagery

</details>

<details>
<summary><strong>Friendly / Playful</strong></summary>

- **Figma** — vibrant multi-color, playful yet professional
- **Zapier** — warm orange, illustration-driven
- **Airtable** — colorful, friendly, structured data

</details>

<details>
<summary><strong>Bold / Cinematic</strong></summary>

- **Binance** — bold yellow accent on monochrome, trading urgency
- **Spotify** — vibrant green on dark, bold type
- **Nike** — monochrome UI, massive uppercase, full-bleed photo

</details>

> Le mode **AUTO** sur l'anchor permet à Claude de choisir parmi les **71 design systems** disponibles sur getdesign.md, pas seulement les 25 présélectionnés.

---

## Tech stack

| Aspect | Détail |
|--------|--------|
| **Langages** | HTML + CSS + JavaScript vanilla |
| **Framework** | Aucun |
| **Build** | Aucun (single file) |
| **Dépendances** | Aucune |
| **Persistence** | `localStorage` (clé `design-md-generator-v1`) |
| **Fonts** | Geist · Instrument Serif · JetBrains Mono (via Google Fonts) |
| **Palette** | Dark warm — `#0A0907` fond, `#E8784A` accent terracotta |
| **Tracker** | Aucun |
| **Cookie** | Aucun |
| **Taille** | ~2 150 lignes, ~80 KB non-minifié |
| **Compatibilité** | Navigateurs récents (Chrome / Firefox / Safari / Edge) |

### Choix de design

- **Brutalist dark warm** — fond chaud (`#0A0907`), pas noir techno
- **Border-radius 0** — sharp edges partout
- **Pairing typographique unusual** — Instrument Serif italique en display + Geist sans en UI + JetBrains Mono en code/preview
- **Accent unique** — terracotta `#E8784A` (clin d'œil à Claude par Anthropic)
- **Grain SVG en overlay** — pour casser le flat

---

## Personnalisation & fork

Tous les **design tokens** sont exposés dans `:root` au début du `<style>`. Tu peux changer la palette, les fonts, les espacements en modifiant 30 lignes :

```css
:root {
  --bg: #0A0907;
  --surface: #13110E;
  --accent: #E8784A;
  --font-display: 'Instrument Serif', Georgia, serif;
  --font-ui: 'Geist', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  /* ... */
}
```

Pour **ajouter un anchor** au dropdown, cherche `<optgroup>` dans le HTML et ajoute :

```html
<option value="slug-getdesign|description courte du système">
  Nom — description visuelle
</option>
```

Pour **modifier la structure du prompt généré**, la fonction `generatePrompt()` dans le `<script>` est la source de vérité. Elle est conditionnelle sur les flags `auto_*` du state.

---

## Roadmap

Idées d'évolutions possibles (PRs bienvenues) :

- [ ] Bouton "Charger un exemple pré-rempli" (notaires / e-commerce / SaaS / éditorial)
- [ ] Toggle Light / Dark mode pour l'outil lui-même
- [ ] Export JSON du brief pour réimport / collaboration
- [ ] Partage par URL (state encodé en query params, no backend)
- [ ] i18n (interface anglaise en plus du français)
- [ ] Mode "Claude Code" — prompt adapté pour `claude code` en CLI plutôt que chat
- [ ] Snippet Raycast / Alfred pour appel rapide depuis n'importe où
- [ ] Génération automatique du `tailwind.config.ts` depuis les tokens choisis
- [ ] Mode "Audit RGAA" — checklist accessibilité injectée dans le prompt

---

## Crédits

- **[getdesign.md](https://getdesign.md)** par [VoltAgent](https://github.com/VoltAgent/awesome-design-md) — la collection de DESIGN.md référencée comme anchors
- **[Claude](https://claude.ai)** par [Anthropic](https://anthropic.com) — l'outil cible des prompts générés
- **Polices** — [Geist](https://vercel.com/font), [Instrument Serif](https://fonts.google.com/specimen/Instrument+Serif), [JetBrains Mono](https://www.jetbrains.com/lp/mono/) (toutes en Google Fonts)

---

## License

[MIT](LICENSE)

Tu peux fork, modifier, héberger, redistribuer librement. Si l'outil te sert, un ⭐ sur le repo est apprécié — mais pas obligatoire.

---

<div align="center">

Construit en France par **[Ludovic Argenty](https://ludovicargenty.com)**
Développeur freelance · Formateur web · Auditeur accessibilité RGAA

[Site](https://ludovicargenty.com) · [LinkedIn](https://www.linkedin.com/in/ludovicargenty/) · [GitHub](https://github.com/[ton-username])

</div>
