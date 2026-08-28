# Contingut del blog de S-IE — "Actualitat i recursos"

Aquest repositori conté **només els articles** de la secció Actualitat i
recursos del web de S-IE. Fer `push` aquí publica els canvis al web
automàticament (via un Deploy Hook de Vercel).

Aquí **no hi ha res del codi del web**: és impossible espatllar la pàgina des
d'aquest repositori.

## Com publicar un article

Llegeix **[INSTRUCCIONS-CODEX.md](./INSTRUCCIONS-CODEX.md)**. En resum:

1. Crea una carpeta dins `articles/` amb un nom net.
2. Posa-hi `ca.mdx` i `es.mdx` (versió catalana i castellana) + la imatge de portada.
3. `git add . && git commit -m "..." && git push`.

## Estructura

```
articles/
  <nom-article>/
    ca.mdx          versió catalana
    es.mdx          versió castellana
    portada.jpg     imatge (opcional)
INSTRUCCIONS-CODEX.md   manual complet
PLANTILLA-ca.mdx        plantilla buida (català)
PLANTILLA-es.mdx        plantilla buida (castellà)
```

## Categories (només aquestes 3)

`actualitat` · `guies` · `normativa`

## Idioma

Cada article ha de tenir **sempre** versió catalana (`ca.mdx`) i castellana
(`es.mdx`).
