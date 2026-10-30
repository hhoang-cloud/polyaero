# Ressources

Liste de ressources : type (PDF, Vidéo, Lien, Fichier 3D…), titre cliquable, détail (taille, durée).

## Règles
- `TITRE_RESSOURCES` : « Ressources », « Pour aller plus loin », « À télécharger ».
- Une ligne par ressource (bloc « Ligne » répété dans `LIGNES`) ; sans détail, laisser le `<span>` vide ou le supprimer.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">{{TITRE_RESSOURCES}}</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    {{LIGNES}}
  </div>
</div>
```

### Ligne

```html
<div style="display: flex; flex-wrap: wrap; align-items: center; gap: 10px; padding: 10px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 auto; display: inline-block; min-width: 48px; text-align: center; padding: 2px 8px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 12px; font-weight: 700;">{{TYPE}}</span>
      <a href="{{URL}}" style="flex: 1 1 200px; font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">{{TITRE}}</a>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">{{DETAIL}}</span>
    </div>
```
