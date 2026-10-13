# Vigie Marques — surveiller sa marque soi-même

Site : https://outils.vread.fr/veille-marques/

Guide et check-list gratuits pour surveiller une marque avec les outils officiels (DATA INPI, BOPI, eSearch plus, TMview),
et explication des délais d'opposition (INPI 2 mois, EUIPO 3 mois). Un produit de READ FRANCE SAS.
Information générale : pas de conseil juridique ; non affilié à l'INPI ni à l'EUIPO.

Téléchargement gratuit (GitHub Releases) : `guide-checklist-surveiller-sa-marque.pdf`

Version payante (veille automatisée des ressemblances, 9 € HT/mois) : **pas encore disponible**, aucune commande possible.

## Mesure d'audience (depuis le 2026-10-13)

`assets/mesure.js` (compteur d'audience anonyme, `v:2`, robots / navigateurs automatisés / `octave_notrack=1` comptés à
part) et `assets/cro.js` (compteurs agrégés de comportement) sont copiés **à l'identique** depuis
`VREAD-corp/octave-checkout` (`gas/web/`, ne jamais modifier les copies). Chargés sur chaque page par `build.py`
(`data-site="veille-marques"`, avec empreinte `?v=`), ils envoient l'action `track` au backend France `octave-pay-gas`, qui
accepte ce site. Clics comptés : PDF gratuits (`free_download`) et page « version payante » (`cta_click`). Aucun cookie,
aucun identifiant, rien sous Do Not Track / GPC ; nos tests ajoutent `?octave_notrack=1`. Détails :
`content/confidentialite.html`. Après une mise à jour du snippet maître : recopier les deux fichiers puis
`node tests/cro.check.mjs assets/cro.js`.

## Structure

- `content/` — pages ; `pdf/` — source HTML du PDF ; `build.py` — générateur statique sans dépendance
- `tests/test_site.py` — vérifications ; `scripts/make_pdf.mjs` — rendu PDF ; `scripts/check_live.mjs` — contrôle en ligne

```sh
python3 build.py && python3 tests/test_site.py
npm i && node scripts/make_pdf.mjs
```

Contenus : CC BY 4.0. Code : MIT. Signaler une erreur : onglet Issues (tickets publics, aucune donnée personnelle).
