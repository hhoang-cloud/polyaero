# Conteneur

Enveloppe obligatoire de toute zone de texte Moodle : police système du thème, largeur 85 % centrée, interligne 1,6.

## Règles
- Une zone « Texte et média » = un seul conteneur ; tous les autres composants vont dedans.
- La largeur reste à 85 % sur tous les écrans (une largeur fixe était trop étroite sur portable).
- Les gabarits l'incluent déjà.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #1d2125; width: 85%; margin: 0 auto 32px auto; box-sizing: border-box; line-height: 1.6;">
  {{CONTENU}}
</div>
```
