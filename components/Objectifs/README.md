# Objectifs

Encadré blanc listant ce que l'apprenant saura faire, avec durée et prérequis.

## Règles
- 2 à 4 objectifs, verbes d'action à l'infinitif (nommer, expliquer, réaliser…).
- Optionnel dans une section courte ; recommandé dans l'accueil et en tête de chapitre.
- Sans durée ni prérequis : supprimer le dernier paragraphe.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="margin: 16px 0; padding: 16px 20px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Objectifs</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    {{OBJECTIFS}}
  </ul>
  <p style="margin: 12px 0 0 0; font-size: 14px; color: #495057;"><strong>Durée</strong> {{DUREE}} · <strong>Prérequis</strong> {{PREREQUIS}}</p>
</div>
```

### Une ligne d'objectif

```html
<li>{{OBJECTIF}}</li>
```
