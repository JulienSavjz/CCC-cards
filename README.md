# Chroma Custom Cards

Collection de cartes personnalisées inspirées de Magic: The Gathering, avec inclinaison 3D et reflets.

## Lancer le projet

```
npm install
npm run dev
```

Build de production : `npm run build` (résultat dans `dist/`).

## Contenu à ajouter dans `public/`

- `cartes/` : les images des cartes (et `0_chroma_backmdit.png`, le dos)
- `favicon.png`

## Ajouter une carte

Ajouter une entrée dans `public/data/cards.json` :
`{ "id": "...", "name": "...", "img": "/cartes/xxx.png", "category": "vintage|original|book-cover|prototype" }`

## Crédits

Fork de [pokemon-cards-css](https://github.com/simeydotme/pokemon-cards-css) par Simon Goellner (GPL-3.0).
Ce projet est distribué sous la même licence (voir `LICENSE`).
