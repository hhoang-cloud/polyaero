# FinSection

Bandeau jaune pâle qui clôt une section : libellé en gras, puis critère de réussite ou invitation à passer à la suite.

## Règles
- `LIBELLE_FIN` : « Mission accomplie » (tutoriel), « Fin du chapitre. », « Point de contrôle : »…
- `TEXTE` : pour une mission, commence par « quand… » et décrit un résultat observable ; pour un chapitre, indique la suite.
- Variante avec bouton quand la suite est une activité (quiz, devoir) ou une autre page.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Simple

```html
<p style="margin: 20px 0 0 0; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;"><strong>{{LIBELLE_FIN}}</strong> {{TEXTE}}</p>
```

### Avec bouton

```html
<div style="margin: 20px 0 0 0; display: flex; flex-wrap: wrap; align-items: center; gap: 12px; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;">
  <p style="flex: 1 1 280px; margin: 0;"><strong>{{LIBELLE_FIN}}</strong> {{TEXTE}}</p>
  <a href="{{URL_SUITE}}" style="flex: 0 0 auto; display: inline-block; padding: 8px 16px; background-color: #0b3b60; color: #ffffff; border-radius: 6px; font-size: 14px; font-weight: 600; text-decoration: none;">{{LIBELLE_SUITE}}</a>
</div>
```
