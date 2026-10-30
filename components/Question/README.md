# Question

Question d'auto-évaluation : la réponse s'affiche au clic (`<details>`), sans JavaScript.

## Règles
- Une question courte, réponse en une phrase.
- Fermée par défaut. Pour un vrai quiz noté, utiliser l'activité Test ou H5P de Moodle et un bouton Accent.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<details style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: center; gap: 12px; padding: 14px 16px; cursor: pointer; list-style: none; outline: none;">
    <span style="flex: 0 0 auto; display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #fcd860; color: #1d2125; font-size: 13px; font-weight: 700;">Question</span>
    <span style="flex: 1 1 auto; font-size: 16px; font-weight: 600; color: #1d2125;">{{QUESTION}}</span>
    <span style="flex: 0 0 auto; font-size: 16px; color: #0b3b60;" title="Voir la réponse">&#9662;</span>
  </summary>
  <div style="padding: 14px 16px; background-color: #f1f3f5; border-top: 1px solid #dee2e6; font-size: 15px;">
    <p style="margin: 0;"><strong>Réponse :</strong> {{REPONSE}}</p>
  </div>
</details>
```
