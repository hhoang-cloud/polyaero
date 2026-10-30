# Integration

Cadre 16:9 adaptatif pour intégrer un fichier HTML (visuel 3D), une vidéo ou un outil externe, avec lien plein écran.

## Règles
- Déposer le fichier HTML comme ressource Fichier (ou dans les fichiers de la zone) et coller son URL `pluginfile.php` dans `URL_FICHIER`.
- Si l'iframe disparaît à l'enregistrement, c'est le nettoyage HTML de Moodle : activer « texte de confiance » (`enabletrusttext`) pour les enseignants ou passer par une ressource Fichier affichée « Intégrée ».
- L'aperçu du design system montre la zone vide (les iframes n'y sont pas autorisées).

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="margin: 16px 0;">
  <div style="position: relative; width: 100%; padding-top: 56.25%; border: 1px solid #dee2e6; border-radius: 8px; overflow: hidden; background-color: #f1f3f5;">
    <iframe src="{{URL_FICHIER}}" title="{{TITRE}}" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;" allow="fullscreen; xr-spatial-tracking" allowfullscreen="" loading="lazy"></iframe>
  </div>
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE}} · <a href="{{URL_FICHIER}}" target="_blank" rel="noopener" style="color: #0b3b60; font-weight: 600;">Ouvrir en plein écran</a></p>
</div>
```
