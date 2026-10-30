# Sommaire

Liste des sections du cours : numéro, titre cliquable, description, durée. À placer dans l'accueil.

## Règles
- `TITRE_SOMMAIRE` : « Votre parcours » pour un tutoriel en missions, « Sommaire » ou « Au programme » pour un cours classique.
- Une ligne par section (bloc « Ligne » répété dans `LIGNES`) ; sans durée, supprimer le dernier `<span>`.
- `LIEN` : URL de la section Moodle (`/course/section.php?id=…`) ou ancre `#section-N`.
- Statique : la progression réelle reste celle de l'achèvement d'activité Moodle.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Code

```html
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">{{TITRE_SOMMAIRE}}</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    {{LIGNES}}
  </div>
</div>
```

### Ligne

```html
<div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">{{N}}</span>
      <div style="flex: 1 1 auto;">
        <a href="{{LIEN}}" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">{{TITRE}}</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">{{DESCRIPTION}}</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">{{DUREE}}</span>
    </div>
```
