# Bouton

Liens en forme de bouton.

## Variantes
- **Primaire** (marine) : l'action principale de la section, une seule.
- **Secondaire** (contour marine) : téléchargement, ressource annexe.
- **Accent** (jaune) : quiz, défi, activité ludique.
- **Lien fléché** : navigation vers la suite.

## Règles
- Libellé court, verbe à l'infinitif.
- Lien vers une activité Moodle : copier l'URL de l'activité dans `URL`.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Primaire

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #0b3b60; color: #ffffff; border: 2px solid #0b3b60; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

### Secondaire

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #ffffff; color: #0b3b60; border: 2px solid #0b3b60; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

### Accent

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #fcd860; color: #1d2125; border: 2px solid #fcd860; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

### Lien fléché

```html
<a href="{{URL}}" style="font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">{{LIBELLE}} &#8594;</a>
```
