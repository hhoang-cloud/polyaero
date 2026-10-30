# Texte

Éléments de texte courant pour les cours classiques : intertitre, paragraphe, listes, mot surligné.

## Règles
- Intertitre : `<h4>` en `marine`, pour découper un chapitre sans carte repliable.
- Paragraphe : 15px, marge basse 12px. Des paragraphes courts, une idée par paragraphe.
- Liste à puces pour une énumération, liste numérotée pour une suite d'actions.
- Surlignage `jaune-pale` : un mot-clé par paragraphe au maximum, jamais une phrase entière.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Intertitre

```html
<h4 style="margin: 28px 0 10px 0; font-size: 19px; font-weight: 700; line-height: 1.3; color: #0b3b60;">{{INTERTITRE}}</h4>
```

### Paragraphe

```html
<p style="margin: 0 0 12px 0; font-size: 15px;">{{TEXTE}}</p>
```

### Liste à puces

```html
<ul style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
  <li>{{POINT}}</li>
</ul>
```

### Liste numérotée

```html
<ol style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
  <li>{{CONSIGNE}}</li>
</ol>
```

### Mot surligné

```html
<mark style="background-color: #fdf6dc; color: #1d2125; padding: 0 3px; border-radius: 3px;">{{MOT}}</mark>
```
