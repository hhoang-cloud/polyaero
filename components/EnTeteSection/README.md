# EnTeteSection

Bandeau d'ouverture d'une section Moodle. Le libellé est libre : **Mission** pour un tutoriel, **Chapitre**, **Module**, **Séance**, **Partie** pour un cours classique.

## Variantes
- **Numérotée** : libellé et numéro jaune dans la colonne `marine-fonce`, titre et accroche à droite.
- **Simple** : sans numéro, libellé jaune au-dessus du titre. Pour une introduction, une annexe, un glossaire, une évaluation.

## Règles
- `LIBELLE` : un seul mot, le même dans tout le cours.
- `NUMERO` sur deux chiffres (01, 02…).
- `TITRE` : un groupe nominal (« Les forces qui s'exercent sur un avion ») ou un verbe à l'infinitif pour une tâche (« Ajouter l'extension… »).
- `ACCROCHE` : une ou deux phrases, ce que la section apporte.
- Pas d'étiquettes ni d'infos supplémentaires dans le bandeau : rester épuré.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Numérotée

```html
<div style="display: flex; flex-wrap: wrap; background-color: #0b3b60; color: #ffffff; border-radius: 10px; overflow: hidden; margin-bottom: 16px;">
  <div style="flex: 0 0 110px; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 18px 12px; text-align: center; background-color: #082c48;">
    <span style="font-size: 12px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #ffffff;">{{LIBELLE}}</span>
    <span style="font-size: 44px; font-weight: 800; line-height: 1; color: #fcd860;">{{NUMERO}}</span>
  </div>
  <div style="flex: 1 1 320px; padding: 18px 24px;">
    <h3 style="margin: 0 0 6px 0; font-size: 22px; font-weight: 700; line-height: 1.3; color: #ffffff;">{{TITRE}}</h3>
    <p style="margin: 0; font-size: 15px; color: #ffffff;">{{ACCROCHE}}</p>
  </div>
</div>
```

### Simple

```html
<div style="background-color: #0b3b60; color: #ffffff; border-radius: 10px; padding: 18px 24px; margin-bottom: 16px;">
  <p style="margin: 0 0 4px 0; font-size: 12px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #fcd860;">{{LIBELLE}}</p>
  <h3 style="margin: 0 0 6px 0; font-size: 22px; font-weight: 700; line-height: 1.3; color: #ffffff;">{{TITRE}}</h3>
  <p style="margin: 0; font-size: 15px; color: #ffffff;">{{ACCROCHE}}</p>
</div>
```
