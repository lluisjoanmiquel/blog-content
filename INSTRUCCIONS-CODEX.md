# Manual per publicar articles (llegeix-me abans de crear res)

Aquest repositori conté **només els articles** de la secció "Actualitat i
recursos" del web de S-IE. Escriure aquí i fer `git push` publica l'article
automàticament al web. **No hi ha res del codi del web en aquest repo**, així que
és impossible espatllar la pàgina des d'aquí.

> IMPORTANT: segueix aquestes regles al peu de la lletra. Si un article no les
> compleix, s'ometrà en silenci i **no es publicarà**.

---

## 1. Les úniques 3 categories que existeixen

Cada article ha de pertànyer a **una** d'aquestes tres categories. Al frontmatter
s'hi posa la **clau** (columna esquerra), sempre igual, mai el nom visible:

| Clau (`category:`) | Nom CA     | Nom ES     |
| ------------------ | ---------- | ---------- |
| `actualitat`       | Actualitat | Actualidad |
| `guies`            | Guies      | Guías      |
| `normativa`        | Normativa  | Normativa  |

No inventis categories noves. Si cap no encaixa, fes servir `actualitat`.

---

## 2. Estructura de carpetes (obligatòria)

Cada article és una **carpeta** dins `articles/`, amb **dues versions** (català i
castellà) i les seves imatges:

```
articles/
└─ nom-carpeta-de-larticle/        ← "translationKey": uneix les dues versions
   ├─ ca.mdx                       ← versió en CATALÀ  (obligatòria)
   ├─ es.mdx                       ← versió en CASTELLÀ (obligatòria)
   └─ portada.jpg                  ← imatge de portada (opcional però recomanada)
```

Regles:

- El **nom de la carpeta** és intern (no surt a la URL). Fes-lo descriptiu i net:
  minúscules, guions, sense accents. Ex: `etiquetatge-gs1-bones-practiques`.
- **Sempre** els dos fitxers: `ca.mdx` i `es.mdx`. El web és bilingüe.
- Les imatges van **dins la mateixa carpeta** de l'article.

---

## 3. El frontmatter (la capçalera de cada `.mdx`)

Tot article comença amb aquest bloc entre `---`. Aquests són els camps:

```yaml
---
title: "Títol de l'article (pot portar accents i majúscules)"
description: "Resum d'1-2 frases. Surt a Google i a les targetes. 120-160 caràcters."
category: guies              # actualitat | guies | normativa
slug: etiquetatge-gs1        # ← el tros final de la URL. LLEGEIX la secció 4.
date: 2026-08-28             # AAAA-MM-DD
author: Equip S-IE           # opcional
cover: portada.jpg           # opcional: nom del fitxer d'imatge d'aquesta carpeta
draft: false                 # true = no es publica (esborrany)
---
```

- `title`, `description`, `category`, `slug` i `date` són **obligatoris**.
- Si en falta algun o és invàlid, l'article **no es publica**.
- `ca.mdx` i `es.mdx` han de tenir la **mateixa `category`**.

---

## 4. Regla d'or: URLs netes (`slug`)

El `slug` és el que surt a la URL, i **és diferent en cada idioma**:

- CA: `https://s-ie.cat/guies/<slug-del-ca.mdx>`
- ES: `https://s-ie.cat/es/guias/<slug-del-es.mdx>`

El `slug` **HA** de ser net:

- només **minúscules**, **números** i **guions** (`-`)
- **sense accents ni ç** → `etiquetatge`, no `etiquetatgé`; `informacio`, no `informació`
- **sense espais, barres, punts ni símbols**
- paraules separades per guions

✅ Bé: `com-triar-impressora-etiquetes`
❌ Malament: `Com triar impressora`, `guía_gs1`, `normativa/2026`, `què-és-gs1`

No facis servir mai un `slug` igual que una secció del web (com `hardware`,
`software`, `partners`, `contacte`…): l'article s'ometrà.

---

## 5. Com s'escriu el cos (Markdown)

Sota el frontmatter, escriu en **Markdown normal**. Amb això n'hi ha prou:

```markdown
Paràgraf d'introducció.

## Un apartat

Text amb **negreta**, _cursiva_ i un [enllaç intern](/contacte).

- punt de llista
- un altre punt

## Un altre apartat

> Una cita destacada.

| Columna A | Columna B |
| --------- | --------- |
| valor 1   | valor 2   |
```

Consells:

- Fes servir `##` per als apartats principals i `###` per als subapartats.
  **No** facis servir `#` (el títol gran ja surt del `title`).
- Enllaços interns del web: comencen per `/` (ex: `/contacte`, `/es/contacto`,
  `/hardware`). Els externs, amb `https://…`.
- Per posar una imatge dins el text: primer copia el fitxer a la carpeta de
  l'article i després `![text alternatiu](nom-imatge.jpg)`.

---

## 6. Publicar

Quan l'article estigui llest:

```bash
git add .
git commit -m "Nou article: <títol>"
git push
```

En un parell de minuts l'article apareix publicat al web. No cal fer res més.

Per treballar sense publicar encara, posa `draft: true` al frontmatter (o no
facis `push` fins que estigui llest).

---

## 7. Checklist abans de fer push

- [ ] Carpeta dins `articles/` amb nom net (minúscules i guions)
- [ ] Existeixen **`ca.mdx` i `es.mdx`**
- [ ] Els dos tenen `title`, `description`, `category`, `slug`, `date`
- [ ] La `category` és una de les 3 vàlides i **igual** als dos fitxers
- [ ] Els `slug` són nets (minúscules, guions, sense accents) i diferents CA/ES
- [ ] Si hi ha `cover`, el fitxer d'imatge és a la mateixa carpeta
- [ ] El cos està en Markdown, amb `##` per als apartats

Tens un exemple complet i funcional a
`articles/etiquetatge-gs1-bones-practiques/` i una plantilla buida a
`PLANTILLA-ca.mdx` / `PLANTILLA-es.mdx`.
