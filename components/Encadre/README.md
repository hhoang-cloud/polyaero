# Encadre

Trois encadrés de mise en avant, fond pâle et barre à gauche.

## Variantes
- **Info** (« À savoir ») : barre `marine`, fond `info-pale`. Pour les « Info : », « Remarque : » du support.
- **Astuce** : barre `jaune`, fond `jaune-pale`. Pour les « Conseil », « Astuce ».
- **Attention** : barre `orange`, fond `orange-pale`, titre `orange-texte`. Pour les « ATTENTION », règles de sécurité.

## Règles
- Une phrase ou deux ; jamais deux encadrés à la suite.
- Le titre porte le sens, la couleur n'est qu'un repère. Le titre peut changer (« Sécurité », « Remarque »), la couleur suit le niveau.

## Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Info

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #eaf1f7; border-left: 4px solid #0b3b60; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #0b3b60;">À savoir</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```

### Astuce

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #fdf6dc; border-left: 4px solid #fcd860; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #1d2125;">Astuce</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```

### Attention

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #fdf1e6; border-left: 4px solid #d4691a; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #8a4210;">Attention</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```
