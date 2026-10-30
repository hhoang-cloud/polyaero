# Exercice

Exercice d'application : énoncé visible, correction affichée au clic (`<details>`), sans JavaScript.

## Règles
- `NUMERO` : numérotation dans la section (1, 2…).
- `CORRECTION` : un ou plusieurs paragraphes, une liste, une image.
- Plus court qu'un exercice ? Utiliser `Question`. Noté ? Utiliser l'activité Test ou Devoir de Moodle avec un `Bouton` accent.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <div style="padding: 14px 18px;">
    <p style="margin: 0 0 8px 0;"><span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #0b3b60; color: #ffffff; font-size: 13px; font-weight: 700;">Exercice {{NUMERO}}</span></p>
    <p style="margin: 0; font-size: 15px;">{{ENONCE}}</p>
  </div>
  <details style="border-top: 1px solid #dee2e6;">
    <summary style="padding: 10px 18px; cursor: pointer; list-style: none; outline: none; font-size: 14px; font-weight: 600; color: #0b3b60;">Voir la correction &#9662;</summary>
    <div style="padding: 0 18px 14px 18px; font-size: 15px;">
      {{CORRECTION}}
    </div>
  </details>
</div>
```
