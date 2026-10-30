# Design system Polyaéro Moodle

Ce dossier contient le design system des cours Moodle POLYAERO.

- Lire `DESIGN_SYSTEM.md` avant de générer ou modifier du HTML de cours Moodle : principes, couleurs, règles TinyMCE, correspondances PDF → composants, et le code de chaque composant.
- Le code HTML doit utiliser uniquement du CSS inline (pas de `<style>`, pas de `<script>`), la classe `img-fluid` sur les images, et être enveloppé dans le composant `Conteneur` (largeur 85 %).
- Les couleurs viennent de `tokens.json` (marine #0b3b60, jaune #fcd860…) : ne pas en inventer d'autres.
- Remplacer tous les `{{…}}` des snippets ; ne jamais laisser d'URL `draftfile.php`.
- Aperçus visuels : `components/<Nom>/preview.html` (s'ouvrent dans un navigateur).
