# Tableau

Tableau à en-tête marine souligné, lignes séparées par un filet ; défile horizontalement sur mobile.

## Règles
- Pour comparer, classer ou lister (blocs, paramètres, caractéristiques).
- Ajouter des colonnes en répétant `<th>` et `<td>` avec les mêmes styles.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="overflow-x: auto; margin: 16px 0;">
  <table style="width: 100%; border-collapse: collapse; font-size: 15px;">
    <thead>
      <tr><th style="text-align: left; padding: 10px 12px; border-bottom: 2px solid #0b3b60; color: #0b3b60; font-weight: 700;">{{COL_1}}</th><th style="text-align: left; padding: 10px 12px; border-bottom: 2px solid #0b3b60; color: #0b3b60; font-weight: 700;">{{COL_2}}</th></tr>
    </thead>
    <tbody>
      {{LIGNES}}
    </tbody>
  </table>
</div>
```

### Ligne

```html
<tr><td style="padding: 10px 12px; border-bottom: 1px solid #dee2e6; vertical-align: top;">{{A}}</td><td style="padding: 10px 12px; border-bottom: 1px solid #dee2e6; vertical-align: top;">{{B}}</td></tr>
```
