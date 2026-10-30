# Etape

Carte repliable (`<details>`) pour découper une section : étape d'une procédure, partie d'un chapitre, approfondissement.

## Variantes
- **Numérotée** : numéro jaune sur marine. Pour une procédure ou une suite ordonnée (étapes 1, 2, 3 ou parties A, B, C).
- **Titre seul** : sans numéro. Pour une notion, un approfondissement (« Pour aller plus loin »), une partie de cours non ordonnée.

## Règles
- `CONTENU` : texte, listes, images, encadrés, définitions, exercices…
- Ouverte par défaut (`open=""`) ; retirer `open=""` pour un contenu facultatif.
- Dans un cours classique, on peut aussi s'en passer et enchaîner les contenus avec des intertitres (`Texte`).

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Numérotée

```html
<details open="" style="margin-top: 16px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: stretch; cursor: pointer; list-style: none; outline: none; background-color: #f1f3f5;">
    <span style="flex: 0 0 48px; display: flex; align-items: center; justify-content: center; background-color: #0b3b60; color: #fcd860; font-size: 18px; font-weight: 800;">{{NUMERO}}</span>
    <span style="flex: 1 1 auto; padding: 12px 16px; font-size: 17px; font-weight: 700; color: #0b3b60;">{{TITRE}}</span>
    <span style="flex: 0 0 auto; padding: 12px 16px; font-size: 16px; color: #0b3b60; align-self: center;" title="Afficher / masquer">&#9662;</span>
  </summary>
  <div style="padding: 18px 24px;">
    {{CONTENU}}
  </div>
</details>
```

### Titre seul

```html
<details open="" style="margin-top: 16px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: center; cursor: pointer; list-style: none; outline: none; background-color: #f1f3f5;">
    <span style="flex: 1 1 auto; padding: 12px 16px; font-size: 17px; font-weight: 700; color: #0b3b60;">{{TITRE}}</span>
    <span style="flex: 0 0 auto; padding: 12px 16px; font-size: 16px; color: #0b3b60;" title="Afficher / masquer">&#9662;</span>
  </summary>
  <div style="padding: 18px 24px;">
    {{CONTENU}}
  </div>
</details>
```
