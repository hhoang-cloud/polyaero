# EnTeteCours

Bandeau marine en tête de la section d'accueil du cours : surtitre jaune, titre, accroche d'une phrase, infos pratiques.

## Règles
- Un seul par cours, dans la section 0 (accueil).
- `SURTITRE` : « Formation », « Cours », « Module », « Tutoriel »…
- `INFOS` : nombre de sections, durée totale, niveau, séparés par « · ».
- Texte blanc sur `marine` (11,6:1) ; surtitre `jaune` (8,4:1).

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="background-color: #0b3b60; color: #ffffff; border-radius: 10px; padding: 28px 32px; margin-bottom: 24px;">
  <p style="margin: 0 0 6px 0; font-size: 13px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #fcd860;">{{SURTITRE}}</p>
  <h2 style="margin: 0 0 10px 0; font-size: 28px; font-weight: 700; line-height: 1.25; color: #ffffff;">{{TITRE}}</h2>
  <p style="margin: 0 0 16px 0; font-size: 16px; color: #ffffff;">{{ACCROCHE}}</p>
  <p style="margin: 0; font-size: 14px; color: #ffffff;">{{INFOS}}</p>
</div>
```
