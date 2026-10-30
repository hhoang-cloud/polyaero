# Image

Capture d'écran, schéma ou photo avec légende ; variante à deux images côte à côte (passent l'une sous l'autre sur mobile).

## Règles
- Toujours un `alt` descriptif et une légende courte (« Figure 1 · … »).
- Uploader l'image avec le bouton image de TinyMCE : jamais d'URL `draftfile.php` (brouillon temporaire invisible pour les étudiants).
- Pas d'attributs `width`/`height` fixes.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Une image

```html
<div style="margin: 16px 0;">
  <img class="img-fluid" src="{{URL_IMAGE}}" alt="{{ALT}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE}}</p>
</div>
```

### Deux images

```html
<div style="display: flex; flex-wrap: wrap; gap: 16px; margin: 16px 0;">
  <div style="flex: 1 1 280px;">
    <img class="img-fluid" src="{{URL_IMAGE_1}}" alt="{{ALT_1}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
    <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE_1}}</p>
  </div>
  <div style="flex: 1 1 280px;">
    <img class="img-fluid" src="{{URL_IMAGE_2}}" alt="{{ALT_2}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
    <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE_2}}</p>
  </div>
</div>
```
