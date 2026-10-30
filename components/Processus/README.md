# Processus

Suite horizontale de blocs reliés par des flèches, sur fond gris ; passe à la ligne sur mobile.

## Règles
- Pour une logique, un cycle ou un ordre (« Nouvelle étape → Condition → … », « Admission → Compression → Combustion → Échappement »), 3 à 7 blocs.
- Un « Bloc » et une « Flèche » répétés dans `BLOCS`.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin: 16px 0; padding: 16px; background-color: #f1f3f5; border-radius: 8px;">
  {{BLOCS}}
</div>
```

### Bloc

```html
<span style="display: inline-block; padding: 8px 14px; border: 1px solid #dee2e6; border-radius: 6px; background-color: #ffffff; font-size: 14px; font-weight: 600; color: #0b3b60;">{{ETAPE}}</span>
```

### Flèche

```html
<span style="font-size: 16px; color: #495057;" aria-hidden="true">&#8594;</span>
```
