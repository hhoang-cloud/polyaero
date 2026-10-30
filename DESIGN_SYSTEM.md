# Polyaéro Moodle — design system (version complète en un fichier)
Fichier généré à partir du design system « Polyaéro Moodle ». Composants HTML à CSS inline pour TinyMCE (Moodle).

---
Polyaéro Moodle est le design system des cours en ligne du centre d'excellence POLYAERO Hautes-Alpes sur Moodle (polyaero.ai, thème eLearningTouch, éditeur TinyMCE). Il sert à mettre en forme tous les types de cours : un **tutoriel** pas à pas organisé en missions, comme un **cours classique** organisé en chapitres, modules ou séances. Les composants sont des briques pédagogiques indépendantes, à assembler selon le contenu.

Tous les composants sont du **HTML avec CSS inline**, à coller dans TinyMCE. Il n'y a ni feuille de style ni JavaScript à charger.

## Principes

- **Épuré.** Blanc, bleu marine, une touche de jaune. Pas d'étiquettes dans les bandeaux, jamais deux encadrés à la suite, une seule action primaire par section.
- **Flexible.** Une section Moodle s'ouvre par un `EnTeteSection` dont le libellé suit le cours : Mission, Chapitre, Module, Séance, Partie. Le reste se compose librement avec les briques de contenu et d'activité.
- **Pédagogique par la structure, pas par la décoration.** Objectifs en tête, notions illustrées (définition, exemple, image), mise en pratique (exercice, question), synthèse (à retenir), clôture (fin de section). La progression réelle passe par l'achèvement d'activité Moodle.
- **Le texte d'origine n'apparaît qu'une fois.** Pas de titre répété dans le contenu.

## Deux façons d'organiser un cours

| | Tutoriel | Cours classique |
| --- | --- | --- |
| Pour | une procédure, un logiciel, une manipulation | des notions, de la théorie, de la réglementation |
| Section | `EnTeteSection` « Mission » | `EnTeteSection` « Chapitre », « Module », « Séance »… |
| Corps | `Etape` numérotées, `Chemin`, `Image`, `Encadre` | `Texte` (intertitres, paragraphes), `Definition`, `Exemple`, `Image`, `Tableau`, `Etape` (titre seul) pour replier une partie |
| Mise en pratique | `Question`, point de contrôle | `Exercice`, `Question`, activité Test |
| Clôture | `FinSection` « Mission accomplie quand… » | `ARetenir`, `Ressources`, `FinSection` « Fin du chapitre. » |
| Gabarit | `GabaritTutoriel` | `GabaritChapitre` |

Les deux se mélangent : un chapitre peut contenir une procédure en `Etape` numérotées, un tutoriel peut avoir une `Definition` ou une section « Annexe » en `EnTeteSection` simple.

## Contenu et ton

- Français, au « vous » : « Ouvrez la fenêtre Marketplace des extensions. »
- Titres de section : un groupe nominal pour une notion (« Les forces qui s'exercent sur un avion »), un verbe à l'infinitif pour une tâche (« Ajouter l'extension SkrTrainingLibrary »).
- Paragraphes courts, une idée par paragraphe ; consignes une action par ligne, en liste numérotée.
- Noms d'éléments d'interface en gras (**Add to Experience**), chemins et raccourcis avec `Chemin`.
- Pas d'emoji, pas de points d'exclamation.

## Couleurs

| Token | Valeur | Rôle |
| --- | --- | --- |
| `marine` | #0b3b60 | Bandeaux, numéros, titres, intertitres, bouton primaire |
| `marine-fonce` | #082c48 | Bloc du numéro de section |
| `jaune` | #fcd860 | Accent : numéros, étiquettes, bouton accent |
| `jaune-pale` | #fdf6dc | Encadré Astuce, fin de section, mot surligné |
| `gris-fond` | #f1f3f5 | En-têtes d'étape, À retenir, Processus, correction |
| `bordure` | #dee2e6 | Bordures et filets |
| `texte` / `texte-secondaire` | #1d2125 / #495057 | Texte courant / légendes, durées |
| `info-pale` | #eaf1f7 | Encadré Info, Definition |
| `orange` / `orange-pale` / `orange-texte` | #d4691a / #fdf1e6 / #8a4210 | Encadré Attention |

- Texte blanc uniquement sur `marine` et `marine-fonce`. Jamais de blanc sur `jaune`.
- Le jaune est un accent : numéros, une étiquette, un bouton de quiz, la fin de section, un mot surligné. Jamais en grand aplat.
- Les valeurs ont été relevées sur des captures de polyaero.ai ; à confirmer avec les réglages du thème eLearningTouch.

## Typographie

- Police système du thème Moodle (`sans`) : pas de fichier à charger, rendu identique au reste de la plateforme. `mono` pour les chemins et touches.
- Hiérarchie : `titre-cours` 28px, `titre-section` 22px, `intertitre` 19px, `titre-etape` 17px, tous en gras ; `surtitre` 13px en majuscules espacées ; `texte` 15px, interligne 1,6.

## Mise en page

- Chaque zone « Texte et média » est un `Conteneur` : largeur `largeur-conteneur` (85 %) sur tous les écrans, centré.
- Écart vertical entre composants : `space-4` (16px). Padding des cartes : `space-5` (24px).
- Coins arrondis : `radius-bandeau` pour les bandeaux, `radius-carte` pour les cartes, `radius-image` pour images et boutons, `radius-petit` pour encadrés et étiquettes.
- Pas d'ombre ni de dégradé. Les cartes sont séparées par une `bordure` de 1px.
- Tout passe à une colonne sur mobile (flex-wrap) : aucun réglage à faire.

## Iconographie

Pas de jeu d'icônes ni d'emoji. Deux caractères seulement, fonctionnels : ▾ (`&#9662;`) pour ce qui se replie, → (`&#8594;`) pour les liens de suite et le `Processus`. Les numéros en jaune tiennent lieu d'ornement.

## Images

- Captures d'écran, schémas ou photos, uploadés avec le bouton image de TinyMCE, avec un `alt` descriptif et une légende courte (`Image`).
- Jamais d'URL `draftfile.php` : c'est un brouillon temporaire, invisible pour les étudiants.
- Pas d'attributs `width` / `height` fixes ; la classe `img-fluid` et `max-width: 100%` gèrent la taille.
- Logo POLYAERO (groupe Logos) : seulement si un document l'exige ; le bandeau de cours suffit en général.

## Règles techniques (TinyMCE)

- **CSS inline uniquement**, dans l'attribut `style`. Pas de balise `<style>`, pas de `<script>` : le nettoyage HTML de Moodle les supprime.
- Seule classe utilisée : `img-fluid` sur les images.
- `<details>` / `<summary>` pour tout ce qui se replie (Etape, Question, correction d'Exercice) : aucun JavaScript.
- Coller le code en mode code source de TinyMCE (`</>`), puis remplacer les `{{…}}`.
- Fichiers HTML (visuels 3D) : composant `Integration`, cadre 16:9. Si l'iframe disparaît à l'enregistrement, activer le texte de confiance pour les enseignants ou utiliser une ressource Fichier affichée « Intégrée ».

## Structure d'un cours

1. **Section 0 · Accueil** : `GabaritAccueil` (EnTeteCours, Objectifs, Sommaire, Encadre Info).
2. **Une section par mission, chapitre ou module** : `GabaritTutoriel` ou `GabaritChapitre`, ou un assemblage libre qui commence par `EnTeteSection` et finit par `FinSection`.
3. **Évaluation** : activité Test, Devoir ou H5P, ouverte par un `Bouton` accent ou une `FinSection` avec bouton.

Dans Moodle : activer l'achèvement d'activité sur chaque section et, si besoin, restreindre l'accès à la section suivante tant que la précédente n'est pas terminée.

## Conversion PDF → HTML (plugin)

Le plugin de conversion (Mistral) choisit d'abord le **type de cours** : tutoriel si le support est une procédure (consignes à l'impératif, captures d'écran, chemins), cours classique sinon. Le formateur peut l'imposer. Puis il applique ces correspondances :

| Dans le PDF | Composant |
| --- | --- |
| Titre du document | `EnTeteCours` (`TITRE`) |
| Table des matières | `Sommaire` (une ligne par partie de premier niveau) |
| Partie de premier niveau (I/, 1., Chapitre…) | Une section : `EnTeteSection`, libellé Mission (tutoriel) ou Chapitre (cours) |
| Introduction, annexe, glossaire | `EnTeteSection` simple |
| Sous-partie d'une procédure (1. 2., a. b.) | `Etape` numérotée |
| Sous-partie d'un cours | `Texte` intertitre, ou `Etape` titre seul si elle est longue |
| Paragraphes, listes | `Texte` |
| « Définition : », terme défini | `Definition` |
| « Exemple : », « Par exemple » | `Exemple` |
| « Exercice », « Application » | `Exercice` (correction si le support la donne) |
| « ATTENTION : », règle de sécurité | `Encadre` Attention |
| « Info : », « Remarque : » | `Encadre` Info |
| « Conseil : », « Astuce : » | `Encadre` Astuce |
| Chemin entre « » ou avec des `/` ou `>` | `Chemin` (chemin) |
| Raccourci (Ctrl+Maj+S) | `Chemin` (touche), une par touche |
| Logique ou cycle « A → B → C » | `Processus` |
| Capture, schéma, photo | `Image` (alt et légende tirés du texte voisin) |
| Tableau | `Tableau` |
| « Résumé », « À retenir », conclusion | `ARetenir` |
| Bibliographie, liens, documents annexes | `Ressources` |
| « Le résultat devrait ressembler à… » | `Image` + texte de `FinSection` |

Le plugin ajoute ensuite, sans inventer de contenu technique, une `FinSection` par section. Il peut proposer des `Objectifs`, une `Question` et un `ARetenir`, à faire valider par le formateur.

## Checklist avant publication

- Chaque zone est dans un `Conteneur`.
- Un seul `EnTeteSection` et une seule `FinSection` par section ; même libellé (Mission, Chapitre…) dans tout le cours.
- Aucune URL `draftfile.php`, chaque image a un `alt`.
- Pas de texte en double.
- Vérifié sur ordinateur portable et sur mobile.

---

# Composants

## GabaritAccueil

Gabarit de la section d'accueil (section 0), quel que soit le type de cours.

### Ordre
1. `EnTeteCours`
2. `Objectifs`
3. `Sommaire`
4. `Encadre` (Info) : comment suivre le cours

### Code complet (exemple)

```html
<div style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #1d2125; width: 85%; margin: 0 auto 32px auto; box-sizing: border-box; line-height: 1.6;">
  <div style="background-color: #0b3b60; color: #ffffff; border-radius: 10px; padding: 28px 32px; margin-bottom: 24px;">
  <p style="margin: 0 0 6px 0; font-size: 13px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #fcd860;">Formation</p>
  <h2 style="margin: 0 0 10px 0; font-size: 28px; font-weight: 700; line-height: 1.25; color: #ffffff;">Skyreal Training</h2>
  <p style="margin: 0 0 16px 0; font-size: 16px; color: #ffffff;">Créez un scénario de formation en réalité virtuelle : du modèle 3D à la carte de travail digitalisée.</p>
  <p style="margin: 0; font-size: 14px; color: #ffffff;">5 missions · environ 3 h · niveau débutant</p>
</div>
<div style="margin: 16px 0; padding: 16px 20px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Objectifs</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    <li>Préparer un projet Skyreal pour la formation</li>
    <li>Construire un scénario étape par étape</li>
    <li>Afficher une carte de travail digitalisée en VR</li>
  </ul>
  <p style="margin: 12px 0 0 0; font-size: 14px; color: #495057;"><strong>Durée</strong> environ 3 h · <strong>Prérequis</strong> bases de l'éditeur Skyreal</p>
</div>
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Votre parcours</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    <div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">01</span>
      <div style="flex: 1 1 auto;">
        <a href="#" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">Préparer l'environnement</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">Ajouter et vérifier l'extension SkrTrainingLibrary.</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">5 min</span>
    </div>
    <div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">02</span>
      <div style="flex: 1 1 auto;">
        <a href="#" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">Bonnes pratiques</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">Ranger l'Outliner et préparer la scène.</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">10 min</span>
    </div>
    <div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">03</span>
      <div style="flex: 1 1 auto;">
        <a href="#" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">Créer le training</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">Importer les assets et créer les acteurs.</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">40 min</span>
    </div>
    <div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">04</span>
      <div style="flex: 1 1 auto;">
        <a href="#" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">Construire le scénario</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">Initialisation, étapes, conditions et fin.</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">60 min</span>
    </div>
    <div style="display: flex; align-items: center; gap: 14px; padding: 12px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 32px; height: 32px; border-radius: 50%; background-color: #0b3b60; color: #fcd860; font-size: 14px; font-weight: 800; display: flex; align-items: center; justify-content: center;">05</span>
      <div style="flex: 1 1 auto;">
        <a href="#" style="font-size: 16px; font-weight: 700; color: #0b3b60; text-decoration: none;">Carte de travail digitalisée</a>
        <p style="margin: 0; font-size: 14px; color: #495057;">Afficher les consignes sur le board et la tablette.</p>
      </div>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">45 min</span>
    </div>
  </div>
</div>
<div style="margin: 16px 0; padding: 12px 16px; background-color: #eaf1f7; border-left: 4px solid #0b3b60; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #0b3b60;">À savoir</p>
  <p style="margin: 0;">Chaque section se termine par un point de contrôle. Marquez-la comme terminée pour suivre votre progression.</p>
</div>
</div>
```

## GabaritChapitre

Gabarit d'un chapitre de cours classique (notions, définitions, exemples, exercices) : une section Moodle, une zone de texte.

### Ordre (à adapter)
1. `EnTeteSection` (libellé Chapitre, Module, Séance…)
2. `Objectifs`
3. Contenu, dans l'ordre du cours : `Texte` (intertitres, paragraphes), `Definition`, `Image`, `Exemple`, `Encadre`, `Tableau`, `Processus`, `Integration` ; `Etape` (titre seul) pour replier une partie longue
4. `Exercice` ou `Question`
5. `ARetenir`
6. `Ressources` (facultatif)
7. `FinSection`

### Code complet (exemple)

```html
<div style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #1d2125; width: 85%; margin: 0 auto 32px auto; box-sizing: border-box; line-height: 1.6;">
  <div style="display: flex; flex-wrap: wrap; background-color: #0b3b60; color: #ffffff; border-radius: 10px; overflow: hidden; margin-bottom: 16px;">
  <div style="flex: 0 0 110px; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 18px 12px; text-align: center; background-color: #082c48;">
    <span style="font-size: 12px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #ffffff;">Chapitre</span>
    <span style="font-size: 44px; font-weight: 800; line-height: 1; color: #fcd860;">02</span>
  </div>
  <div style="flex: 1 1 320px; padding: 18px 24px;">
    <h3 style="margin: 0 0 6px 0; font-size: 22px; font-weight: 700; line-height: 1.3; color: #ffffff;">Les forces qui s'exercent sur un avion</h3>
    <p style="margin: 0; font-size: 15px; color: #ffffff;">Portance, poids, poussée et traînée : comprendre ce qui maintient un avion en vol.</p>
  </div>
</div>
<div style="margin: 16px 0; padding: 16px 20px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Objectifs</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    <li>Nommer les quatre forces qui s'exercent sur un avion</li>
    <li>Expliquer l'origine de la portance</li>
    <li>Décrire l'équilibre des forces en vol de croisière</li>
  </ul>
  <p style="margin: 12px 0 0 0; font-size: 14px; color: #495057;"><strong>Durée</strong> 30 min · <strong>Prérequis</strong> chapitre 1</p>
</div>
<p style="margin: 0 0 12px 0; font-size: 15px;">Un avion en vol est soumis à quatre forces. Deux sont liées à l'air qui l'entoure, une au moteur, une à la gravité.</p>
<h4 style="margin: 28px 0 10px 0; font-size: 19px; font-weight: 700; line-height: 1.3; color: #0b3b60;">La portance</h4>
<p style="margin: 0 0 12px 0; font-size: 15px;">L'aile dévie l'air vers le bas ; en réaction, l'air exerce sur l'aile une force vers le haut : la <mark style="background-color: #fdf6dc; color: #1d2125; padding: 0 3px; border-radius: 3px;">portance</mark>.</p>
<ul style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
  <li>Elle augmente avec la vitesse.</li>
  <li>Elle augmente avec l'angle d'incidence, jusqu'au décrochage.</li>
</ul>
<div style="margin: 16px 0; padding: 14px 18px; background-color: #eaf1f7; border-radius: 8px; font-size: 15px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Définition</p>
  <p style="margin: 0;"><strong style="color: #0b3b60;">Portance</strong> : force aérodynamique perpendiculaire à l'écoulement de l'air, produite principalement par l'aile.</p>
</div>
<div style="margin: 16px 0;">
  <img class="img-fluid" src="/_blob/0d9f38445a53915b9ab681082891cadf" alt="Avion dans un hangar" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">Figure 1 · Le profil de l'aile produit la portance.</p>
</div>
<div style="margin: 16px 0; padding: 14px 18px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; font-size: 15px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Exemple</p>
  <p style="margin: 0;">En vol de croisière à altitude constante, la portance équilibre exactement le poids de l'avion.</p>
</div>
<div style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <div style="padding: 14px 18px;">
    <p style="margin: 0 0 8px 0;"><span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #0b3b60; color: #ffffff; font-size: 13px; font-weight: 700;">Exercice 1</span></p>
    <p style="margin: 0; font-size: 15px;">Un avion vole en palier, à vitesse constante. Que peut-on dire des quatre forces qui s'exercent sur lui ?</p>
  </div>
  <details style="border-top: 1px solid #dee2e6;">
    <summary style="padding: 10px 18px; cursor: pointer; list-style: none; outline: none; font-size: 14px; font-weight: 600; color: #0b3b60;">Voir la correction &#9662;</summary>
    <div style="padding: 0 18px 14px 18px; font-size: 15px;">
      <p style="margin: 0;">Elles s'équilibrent deux à deux : la portance compense le poids et la poussée compense la traînée.</p>
    </div>
  </details>
</div>
<div style="margin: 24px 0; padding: 16px 20px; background-color: #f1f3f5; border-radius: 8px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">À retenir</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    <li>Quatre forces : portance, poids, poussée, traînée.</li>
    <li>La portance vient de l'aile et dépend de la vitesse et de l'incidence.</li>
    <li>En croisière, les forces s'équilibrent deux à deux.</li>
  </ul>
</div>
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Ressources</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    <div style="display: flex; flex-wrap: wrap; align-items: center; gap: 10px; padding: 10px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 auto; display: inline-block; min-width: 48px; text-align: center; padding: 2px 8px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 12px; font-weight: 700;">PDF</span>
      <a href="#" style="flex: 1 1 200px; font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">Support de cours complet</a>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">2,4 Mo</span>
    </div>
    <div style="display: flex; flex-wrap: wrap; align-items: center; gap: 10px; padding: 10px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 auto; display: inline-block; min-width: 48px; text-align: center; padding: 2px 8px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 12px; font-weight: 700;">Vidéo</span>
      <a href="#" style="flex: 1 1 200px; font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">Démonstration en soufflerie</a>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">6 min</span>
    </div>
    <div style="display: flex; flex-wrap: wrap; align-items: center; gap: 10px; padding: 10px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 auto; display: inline-block; min-width: 48px; text-align: center; padding: 2px 8px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 12px; font-weight: 700;">Lien</span>
      <a href="#" style="flex: 1 1 200px; font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">Glossaire aéronautique</a>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;"></span>
    </div>
  </div>
</div>
<p style="margin: 20px 0 0 0; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;"><strong>Fin du chapitre.</strong> Marquez la section comme terminée et passez au chapitre 3.</p>
</div>
```

## GabaritTutoriel

Gabarit d'une section de tutoriel (procédure logicielle, manipulation) : une mission, des étapes numérotées, un point de contrôle.

### Ordre
1. `EnTeteSection` (libellé Mission)
2. `Objectifs` (facultatif)
3. `Etape` numérotée × n (consignes, `Image`, `Chemin`, `Encadre`, `Processus`, `Integration`)
4. `Question` (facultatif)
5. `ARetenir` (facultatif)
6. `FinSection` (« Mission accomplie quand… »)

### Code complet (exemple)

```html
<div style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #1d2125; width: 85%; margin: 0 auto 32px auto; box-sizing: border-box; line-height: 1.6;">
  <div style="display: flex; flex-wrap: wrap; background-color: #0b3b60; color: #ffffff; border-radius: 10px; overflow: hidden; margin-bottom: 16px;">
  <div style="flex: 0 0 110px; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 18px 12px; text-align: center; background-color: #082c48;">
    <span style="font-size: 12px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #ffffff;">Mission</span>
    <span style="font-size: 44px; font-weight: 800; line-height: 1; color: #fcd860;">01</span>
  </div>
  <div style="flex: 1 1 320px; padding: 18px 24px;">
    <h3 style="margin: 0 0 6px 0; font-size: 22px; font-weight: 700; line-height: 1.3; color: #ffffff;">Ajouter l'extension SkrTrainingLibrary</h3>
    <p style="margin: 0; font-size: 15px; color: #ffffff;">Cette extension contient tous les blocs du training : étapes, conditions, board et cartes de travail.</p>
  </div>
</div>
<details open="" style="margin-top: 16px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: stretch; cursor: pointer; list-style: none; outline: none; background-color: #f1f3f5;">
    <span style="flex: 0 0 48px; display: flex; align-items: center; justify-content: center; background-color: #0b3b60; color: #fcd860; font-size: 18px; font-weight: 800;">1</span>
    <span style="flex: 1 1 auto; padding: 12px 16px; font-size: 17px; font-weight: 700; color: #0b3b60;">Ajouter l'extension depuis la Marketplace</span>
    <span style="flex: 0 0 auto; padding: 12px 16px; font-size: 16px; color: #0b3b60; align-self: center;" title="Afficher / masquer">&#9662;</span>
  </summary>
  <div style="padding: 18px 24px;">
    <ol style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
      <li>Ouvrez la fenêtre <strong>Marketplace</strong> des extensions.</li>
      <li>Repérez la carte <strong>SkrTrainingLibrary</strong>.</li>
      <li>Si elle n'est pas dans la liste, cliquez sur <strong>Add to Experience</strong>.</li>
    </ol>
    <div style="margin: 16px 0;">
  <img class="img-fluid" src="/_blob/0d9f38445a53915b9ab681082891cadf" alt="Fenêtre Marketplace" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">La carte SkrTrainingLibrary dans la Marketplace.</p>
</div>
  </div>
</details>
<details open="" style="margin-top: 16px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: stretch; cursor: pointer; list-style: none; outline: none; background-color: #f1f3f5;">
    <span style="flex: 0 0 48px; display: flex; align-items: center; justify-content: center; background-color: #0b3b60; color: #fcd860; font-size: 18px; font-weight: 800;">2</span>
    <span style="flex: 1 1 auto; padding: 12px 16px; font-size: 17px; font-weight: 700; color: #0b3b60;">Vérifier que l'extension est active</span>
    <span style="flex: 0 0 auto; padding: 12px 16px; font-size: 16px; color: #0b3b60; align-self: center;" title="Afficher / masquer">&#9662;</span>
  </summary>
  <div style="padding: 18px 24px;">
    <p style="margin: 0 0 12px 0; font-size: 15px;">Dans le <strong>Content Browser</strong>, ouvrez <span style="font-family: SFMono-Regular, Consolas, 'Liberation Mono', Menlo, monospace; font-size: 13px; background-color: #f1f3f5; border: 1px solid #dee2e6; border-radius: 4px; padding: 1px 6px; color: #1d2125;">All > Plugins</span> : le dossier <strong>SkrTrainingLibrary</strong> doit apparaître.</p>
    <div style="margin: 16px 0; padding: 12px 16px; background-color: #fdf1e6; border-left: 4px solid #d4691a; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #8a4210;">Attention</p>
  <p style="margin: 0;">Le dossier n'apparaît pas ? Revenez à l'étape 1.</p>
</div>
  </div>
</details>
<details style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: center; gap: 12px; padding: 14px 16px; cursor: pointer; list-style: none; outline: none;">
    <span style="flex: 0 0 auto; display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #fcd860; color: #1d2125; font-size: 13px; font-weight: 700;">Question</span>
    <span style="flex: 1 1 auto; font-size: 16px; font-weight: 600; color: #1d2125;">Où vérifier que l'extension est active ?</span>
    <span style="flex: 0 0 auto; font-size: 16px; color: #0b3b60;" title="Voir la réponse">&#9662;</span>
  </summary>
  <div style="padding: 14px 16px; background-color: #f1f3f5; border-top: 1px solid #dee2e6; font-size: 15px;">
    <p style="margin: 0;"><strong>Réponse :</strong> dans le Content Browser, dossier All > Plugins.</p>
  </div>
</details>
<p style="margin: 20px 0 0 0; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;"><strong>Mission accomplie</strong> quand le dossier est visible. Marquez la section comme terminée et passez à la mission 02.</p>
</div>
```

## Conteneur

Enveloppe obligatoire de toute zone de texte Moodle : police système du thème, largeur 85 % centrée, interligne 1,6.

### Règles
- Une zone « Texte et média » = un seul conteneur ; tous les autres composants vont dedans.
- La largeur reste à 85 % sur tous les écrans (une largeur fixe était trop étroite sur portable).
- Les gabarits l'incluent déjà.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; color: #1d2125; width: 85%; margin: 0 auto 32px auto; box-sizing: border-box; line-height: 1.6;">
  {{CONTENU}}
</div>
```

## EnTeteCours

Bandeau marine en tête de la section d'accueil du cours : surtitre jaune, titre, accroche d'une phrase, infos pratiques.

### Règles
- Un seul par cours, dans la section 0 (accueil).
- `SURTITRE` : « Formation », « Cours », « Module », « Tutoriel »…
- `INFOS` : nombre de sections, durée totale, niveau, séparés par « · ».
- Texte blanc sur `marine` (11,6:1) ; surtitre `jaune` (8,4:1).

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="background-color: #0b3b60; color: #ffffff; border-radius: 10px; padding: 28px 32px; margin-bottom: 24px;">
  <p style="margin: 0 0 6px 0; font-size: 13px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #fcd860;">{{SURTITRE}}</p>
  <h2 style="margin: 0 0 10px 0; font-size: 28px; font-weight: 700; line-height: 1.25; color: #ffffff;">{{TITRE}}</h2>
  <p style="margin: 0 0 16px 0; font-size: 16px; color: #ffffff;">{{ACCROCHE}}</p>
  <p style="margin: 0; font-size: 14px; color: #ffffff;">{{INFOS}}</p>
</div>
```

## EnTeteSection

Bandeau d'ouverture d'une section Moodle. Le libellé est libre : **Mission** pour un tutoriel, **Chapitre**, **Module**, **Séance**, **Partie** pour un cours classique.

### Variantes
- **Numérotée** : libellé et numéro jaune dans la colonne `marine-fonce`, titre et accroche à droite.
- **Simple** : sans numéro, libellé jaune au-dessus du titre. Pour une introduction, une annexe, un glossaire, une évaluation.

### Règles
- `LIBELLE` : un seul mot, le même dans tout le cours.
- `NUMERO` sur deux chiffres (01, 02…).
- `TITRE` : un groupe nominal (« Les forces qui s'exercent sur un avion ») ou un verbe à l'infinitif pour une tâche (« Ajouter l'extension… »).
- `ACCROCHE` : une ou deux phrases, ce que la section apporte.
- Pas d'étiquettes ni d'infos supplémentaires dans le bandeau : rester épuré.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Numérotée

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

#### Simple

```html
<div style="background-color: #0b3b60; color: #ffffff; border-radius: 10px; padding: 18px 24px; margin-bottom: 16px;">
  <p style="margin: 0 0 4px 0; font-size: 12px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: #fcd860;">{{LIBELLE}}</p>
  <h3 style="margin: 0 0 6px 0; font-size: 22px; font-weight: 700; line-height: 1.3; color: #ffffff;">{{TITRE}}</h3>
  <p style="margin: 0; font-size: 15px; color: #ffffff;">{{ACCROCHE}}</p>
</div>
```

## Objectifs

Encadré blanc listant ce que l'apprenant saura faire, avec durée et prérequis.

### Règles
- 2 à 4 objectifs, verbes d'action à l'infinitif (nommer, expliquer, réaliser…).
- Optionnel dans une section courte ; recommandé dans l'accueil et en tête de chapitre.
- Sans durée ni prérequis : supprimer le dernier paragraphe.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 16px 0; padding: 16px 20px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Objectifs</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    {{OBJECTIFS}}
  </ul>
  <p style="margin: 12px 0 0 0; font-size: 14px; color: #495057;"><strong>Durée</strong> {{DUREE}} · <strong>Prérequis</strong> {{PREREQUIS}}</p>
</div>
```

#### Une ligne d'objectif

```html
<li>{{OBJECTIF}}</li>
```

## Sommaire

Liste des sections du cours : numéro, titre cliquable, description, durée. À placer dans l'accueil.

### Règles
- `TITRE_SOMMAIRE` : « Votre parcours » pour un tutoriel en missions, « Sommaire » ou « Au programme » pour un cours classique.
- Une ligne par section (bloc « Ligne » répété dans `LIGNES`) ; sans durée, supprimer le dernier `<span>`.
- `LIEN` : URL de la section Moodle (`/course/section.php?id=…`) ou ancre `#section-N`.
- Statique : la progression réelle reste celle de l'achèvement d'activité Moodle.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">{{TITRE_SOMMAIRE}}</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    {{LIGNES}}
  </div>
</div>
```

#### Ligne

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

## Etape

Carte repliable (`<details>`) pour découper une section : étape d'une procédure, partie d'un chapitre, approfondissement.

### Variantes
- **Numérotée** : numéro jaune sur marine. Pour une procédure ou une suite ordonnée (étapes 1, 2, 3 ou parties A, B, C).
- **Titre seul** : sans numéro. Pour une notion, un approfondissement (« Pour aller plus loin »), une partie de cours non ordonnée.

### Règles
- `CONTENU` : texte, listes, images, encadrés, définitions, exercices…
- Ouverte par défaut (`open=""`) ; retirer `open=""` pour un contenu facultatif.
- Dans un cours classique, on peut aussi s'en passer et enchaîner les contenus avec des intertitres (`Texte`).

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Numérotée

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

#### Titre seul

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

## Texte

Éléments de texte courant pour les cours classiques : intertitre, paragraphe, listes, mot surligné.

### Règles
- Intertitre : `<h4>` en `marine`, pour découper un chapitre sans carte repliable.
- Paragraphe : 15px, marge basse 12px. Des paragraphes courts, une idée par paragraphe.
- Liste à puces pour une énumération, liste numérotée pour une suite d'actions.
- Surlignage `jaune-pale` : un mot-clé par paragraphe au maximum, jamais une phrase entière.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Intertitre

```html
<h4 style="margin: 28px 0 10px 0; font-size: 19px; font-weight: 700; line-height: 1.3; color: #0b3b60;">{{INTERTITRE}}</h4>
```

#### Paragraphe

```html
<p style="margin: 0 0 12px 0; font-size: 15px;">{{TEXTE}}</p>
```

#### Liste à puces

```html
<ul style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
  <li>{{POINT}}</li>
</ul>
```

#### Liste numérotée

```html
<ol style="margin: 0 0 12px 0; padding-left: 22px; font-size: 15px;">
  <li>{{CONSIGNE}}</li>
</ol>
```

#### Mot surligné

```html
<mark style="background-color: #fdf6dc; color: #1d2125; padding: 0 3px; border-radius: 3px;">{{MOT}}</mark>
```

## Definition

Définition d'une notion, sur fond `info-pale`, terme en gras `marine`.

### Règles
- Un terme par encadré, définition en une ou deux phrases.
- Pour un glossaire complet, enchaîner plusieurs définitions dans une section « Annexe ».

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 16px 0; padding: 14px 18px; background-color: #eaf1f7; border-radius: 8px; font-size: 15px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Définition</p>
  <p style="margin: 0;"><strong style="color: #0b3b60;">{{TERME}}</strong> : {{DEFINITION}}</p>
</div>
```

## Exemple

Illustration concrète d'une notion, dans une carte blanche bordée.

### Règles
- Placer l'exemple juste après la notion qu'il illustre.
- Un cas réel du métier (atelier, vol, simulateur) plutôt qu'un cas abstrait.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 16px 0; padding: 14px 18px; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; font-size: 15px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">Exemple</p>
  <p style="margin: 0;">{{EXEMPLE}}</p>
</div>
```

## Image

Capture d'écran, schéma ou photo avec légende ; variante à deux images côte à côte (passent l'une sous l'autre sur mobile).

### Règles
- Toujours un `alt` descriptif et une légende courte (« Figure 1 · … »).
- Uploader l'image avec le bouton image de TinyMCE : jamais d'URL `draftfile.php` (brouillon temporaire invisible pour les étudiants).
- Pas d'attributs `width`/`height` fixes.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Une image

```html
<div style="margin: 16px 0;">
  <img class="img-fluid" src="{{URL_IMAGE}}" alt="{{ALT}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE}}</p>
</div>
```

#### Deux images

```html
<div style="display: flex; flex-wrap: wrap; gap: 16px; margin: 16px 0;">
  <div style="flex: 1 1 280px;">
    <img class="img-fluid" src="{{URL_IMAGE_1}}" alt="{{ALT_1}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
    <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE_1}}</p>
  </div>
  <div style="flex: 1 1 280px;">
    <img class="img-fluid" src="{{URL_IMAGE_2}}" alt="{{ALT_2}}" style="max-width: 100%; height: auto; display: block; border-radius: 6px; border: 1px solid #dee2e6;">
    <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE_2}}</p>
  </div>
</div>
```

## Tableau

Tableau à en-tête marine souligné, lignes séparées par un filet ; défile horizontalement sur mobile.

### Règles
- Pour comparer, classer ou lister (blocs, paramètres, caractéristiques).
- Ajouter des colonnes en répétant `<th>` et `<td>` avec les mêmes styles.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

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

#### Ligne

```html
<tr><td style="padding: 10px 12px; border-bottom: 1px solid #dee2e6; vertical-align: top;">{{A}}</td><td style="padding: 10px 12px; border-bottom: 1px solid #dee2e6; vertical-align: top;">{{B}}</td></tr>
```

## Processus

Suite horizontale de blocs reliés par des flèches, sur fond gris ; passe à la ligne sur mobile.

### Règles
- Pour une logique, un cycle ou un ordre (« Nouvelle étape → Condition → … », « Admission → Compression → Combustion → Échappement »), 3 à 7 blocs.
- Un « Bloc » et une « Flèche » répétés dans `BLOCS`.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="display: flex; flex-wrap: wrap; align-items: center; gap: 8px; margin: 16px 0; padding: 16px; background-color: #f1f3f5; border-radius: 8px;">
  {{BLOCS}}
</div>
```

#### Bloc

```html
<span style="display: inline-block; padding: 8px 14px; border: 1px solid #dee2e6; border-radius: 6px; background-color: #ffffff; font-size: 14px; font-weight: 600; color: #0b3b60;">{{ETAPE}}</span>
```

#### Flèche

```html
<span style="font-size: 16px; color: #495057;" aria-hidden="true">&#8594;</span>
```

## Chemin

Repères en ligne pour les chemins de dossiers, menus et raccourcis clavier.

### Règles
- Chemin : tout chemin de fichier ou de menu (`/SkrTrainingLibrary/…`, `All > Plugins`).
- Touche : une touche par élément, reliées par « + ».
- Les noms de boutons ou de champs de l'interface restent en `<strong>`.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

### Chemin

```html
<span style="font-family: SFMono-Regular, Consolas, 'Liberation Mono', Menlo, monospace; font-size: 13px; background-color: #f1f3f5; border: 1px solid #dee2e6; border-radius: 4px; padding: 1px 6px; color: #1d2125;">{{CHEMIN}}</span>
```

#### Touche

```html
<span style="font-family: SFMono-Regular, Consolas, 'Liberation Mono', Menlo, monospace; font-size: 13px; background-color: #ffffff; border: 1px solid #dee2e6; border-bottom-width: 2px; border-radius: 4px; padding: 1px 6px; color: #1d2125;">{{TOUCHE}}</span>
```

## Integration

Cadre 16:9 adaptatif pour intégrer un fichier HTML (visuel 3D), une vidéo ou un outil externe, avec lien plein écran.

### Règles
- Déposer le fichier HTML comme ressource Fichier (ou dans les fichiers de la zone) et coller son URL `pluginfile.php` dans `URL_FICHIER`.
- Si l'iframe disparaît à l'enregistrement, c'est le nettoyage HTML de Moodle : activer « texte de confiance » (`enabletrusttext`) pour les enseignants ou passer par une ressource Fichier affichée « Intégrée ».
- L'aperçu du design system montre la zone vide (les iframes n'y sont pas autorisées).

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 16px 0;">
  <div style="position: relative; width: 100%; padding-top: 56.25%; border: 1px solid #dee2e6; border-radius: 8px; overflow: hidden; background-color: #f1f3f5;">
    <iframe src="{{URL_FICHIER}}" title="{{TITRE}}" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;" allow="fullscreen; xr-spatial-tracking" allowfullscreen="" loading="lazy"></iframe>
  </div>
  <p style="margin: 6px 0 0 0; font-size: 13px; color: #495057;">{{LEGENDE}} · <a href="{{URL_FICHIER}}" target="_blank" rel="noopener" style="color: #0b3b60; font-weight: 600;">Ouvrir en plein écran</a></p>
</div>
```

## Ressources

Liste de ressources : type (PDF, Vidéo, Lien, Fichier 3D…), titre cliquable, détail (taille, durée).

### Règles
- `TITRE_RESSOURCES` : « Ressources », « Pour aller plus loin », « À télécharger ».
- Une ligne par ressource (bloc « Ligne » répété dans `LIGNES`) ; sans détail, laisser le `<span>` vide ou le supprimer.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 24px 0;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">{{TITRE_RESSOURCES}}</p>
  <div style="border-bottom: 1px solid #dee2e6;">
    {{LIGNES}}
  </div>
</div>
```

#### Ligne

```html
<div style="display: flex; flex-wrap: wrap; align-items: center; gap: 10px; padding: 10px 0; border-top: 1px solid #dee2e6;">
      <span style="flex: 0 0 auto; display: inline-block; min-width: 48px; text-align: center; padding: 2px 8px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 12px; font-weight: 700;">{{TYPE}}</span>
      <a href="{{URL}}" style="flex: 1 1 200px; font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">{{TITRE}}</a>
      <span style="flex: 0 0 auto; font-size: 13px; color: #495057;">{{DETAIL}}</span>
    </div>
```

## Encadre

Trois encadrés de mise en avant, fond pâle et barre à gauche.

### Variantes
- **Info** (« À savoir ») : barre `marine`, fond `info-pale`. Pour les « Info : », « Remarque : » du support.
- **Astuce** : barre `jaune`, fond `jaune-pale`. Pour les « Conseil », « Astuce ».
- **Attention** : barre `orange`, fond `orange-pale`, titre `orange-texte`. Pour les « ATTENTION », règles de sécurité.

### Règles
- Une phrase ou deux ; jamais deux encadrés à la suite.
- Le titre porte le sens, la couleur n'est qu'un repère. Le titre peut changer (« Sécurité », « Remarque »), la couleur suit le niveau.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Info

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #eaf1f7; border-left: 4px solid #0b3b60; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #0b3b60;">À savoir</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```

#### Astuce

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #fdf6dc; border-left: 4px solid #fcd860; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #1d2125;">Astuce</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```

#### Attention

```html
<div style="margin: 16px 0; padding: 12px 16px; background-color: #fdf1e6; border-left: 4px solid #d4691a; border-radius: 4px; font-size: 15px;">
  <p style="margin: 0 0 4px 0; font-size: 14px; font-weight: 700; color: #8a4210;">Attention</p>
  <p style="margin: 0;">{{TEXTE}}</p>
</div>
```

## Exercice

Exercice d'application : énoncé visible, correction affichée au clic (`<details>`), sans JavaScript.

### Règles
- `NUMERO` : numérotation dans la section (1, 2…).
- `CORRECTION` : un ou plusieurs paragraphes, une liste, une image.
- Plus court qu'un exercice ? Utiliser `Question`. Noté ? Utiliser l'activité Test ou Devoir de Moodle avec un `Bouton` accent.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <div style="padding: 14px 18px;">
    <p style="margin: 0 0 8px 0;"><span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #0b3b60; color: #ffffff; font-size: 13px; font-weight: 700;">Exercice {{NUMERO}}</span></p>
    <p style="margin: 0; font-size: 15px;">{{ENONCE}}</p>
  </div>
  <details style="border-top: 1px solid #dee2e6;">
    <summary style="padding: 10px 18px; cursor: pointer; list-style: none; outline: none; font-size: 14px; font-weight: 600; color: #0b3b60;">Voir la correction &#9662;</summary>
    <div style="padding: 0 18px 14px 18px; font-size: 15px;">
      {{CORRECTION}}
    </div>
  </details>
</div>
```

## Question

Question d'auto-évaluation : la réponse s'affiche au clic (`<details>`), sans JavaScript.

### Règles
- Une question courte, réponse en une phrase.
- Fermée par défaut. Pour un vrai quiz noté, utiliser l'activité Test ou H5P de Moodle et un bouton Accent.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<details style="margin: 16px 0; border: 1px solid #dee2e6; border-radius: 8px; background-color: #ffffff; overflow: hidden;">
  <summary style="display: flex; align-items: center; gap: 12px; padding: 14px 16px; cursor: pointer; list-style: none; outline: none;">
    <span style="flex: 0 0 auto; display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #fcd860; color: #1d2125; font-size: 13px; font-weight: 700;">Question</span>
    <span style="flex: 1 1 auto; font-size: 16px; font-weight: 600; color: #1d2125;">{{QUESTION}}</span>
    <span style="flex: 0 0 auto; font-size: 16px; color: #0b3b60;" title="Voir la réponse">&#9662;</span>
  </summary>
  <div style="padding: 14px 16px; background-color: #f1f3f5; border-top: 1px solid #dee2e6; font-size: 15px;">
    <p style="margin: 0;"><strong>Réponse :</strong> {{REPONSE}}</p>
  </div>
</details>
```

## ARetenir

Synthèse des points clés d'une section, sur fond gris, avant la fin de section.

### Règles
- 2 à 4 points, phrases courtes.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Code

```html
<div style="margin: 24px 0; padding: 16px 20px; background-color: #f1f3f5; border-radius: 8px;">
  <p style="margin: 0 0 8px 0; font-size: 13px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: #0b3b60;">À retenir</p>
  <ul style="margin: 0; padding-left: 20px; font-size: 15px;">
    {{POINTS}}
  </ul>
</div>
```

## FinSection

Bandeau jaune pâle qui clôt une section : libellé en gras, puis critère de réussite ou invitation à passer à la suite.

### Règles
- `LIBELLE_FIN` : « Mission accomplie » (tutoriel), « Fin du chapitre. », « Point de contrôle : »…
- `TEXTE` : pour une mission, commence par « quand… » et décrit un résultat observable ; pour un chapitre, indique la suite.
- Variante avec bouton quand la suite est une activité (quiz, devoir) ou une autre page.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Simple

```html
<p style="margin: 20px 0 0 0; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;"><strong>{{LIBELLE_FIN}}</strong> {{TEXTE}}</p>
```

#### Avec bouton

```html
<div style="margin: 20px 0 0 0; display: flex; flex-wrap: wrap; align-items: center; gap: 12px; padding: 12px 16px; background-color: #fdf6dc; border-radius: 8px; font-size: 15px;">
  <p style="flex: 1 1 280px; margin: 0;"><strong>{{LIBELLE_FIN}}</strong> {{TEXTE}}</p>
  <a href="{{URL_SUITE}}" style="flex: 0 0 auto; display: inline-block; padding: 8px 16px; background-color: #0b3b60; color: #ffffff; border-radius: 6px; font-size: 14px; font-weight: 600; text-decoration: none;">{{LIBELLE_SUITE}}</a>
</div>
```

## Bouton

Liens en forme de bouton.

### Variantes
- **Primaire** (marine) : l'action principale de la section, une seule.
- **Secondaire** (contour marine) : téléchargement, ressource annexe.
- **Accent** (jaune) : quiz, défi, activité ludique.
- **Lien fléché** : navigation vers la suite.

### Règles
- Libellé court, verbe à l'infinitif.
- Lien vers une activité Moodle : copier l'URL de l'activité dans `URL`.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Primaire

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #0b3b60; color: #ffffff; border: 2px solid #0b3b60; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

#### Secondaire

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #ffffff; color: #0b3b60; border: 2px solid #0b3b60; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

#### Accent

```html
<a href="{{URL}}" style="display: inline-block; padding: 10px 18px; background-color: #fcd860; color: #1d2125; border: 2px solid #fcd860; border-radius: 6px; font-size: 15px; font-weight: 600; text-decoration: none;">{{LIBELLE}}</a>
```

#### Lien fléché

```html
<a href="{{URL}}" style="font-size: 15px; font-weight: 600; color: #0b3b60; text-decoration: none;">{{LIBELLE}} &#8594;</a>
```

## Etiquette

Étiquettes courtes (durée, statut, niveau).

### Règles
- Un à trois mots. Neutre par défaut ; jaune pour signaler une nouveauté ; marine pour un repère fort.
- À utiliser avec parcimonie : pas dans les bandeaux de section.

### Code à copier

CSS inline uniquement. Remplacer les `{{…}}`.

#### Neutre

```html
<span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #f1f3f5; color: #0b3b60; font-size: 13px; font-weight: 600;">{{TEXTE}}</span>
```

#### Jaune

```html
<span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #fcd860; color: #1d2125; font-size: 13px; font-weight: 600;">{{TEXTE}}</span>
```

#### Marine

```html
<span style="display: inline-block; padding: 2px 10px; border-radius: 4px; background-color: #0b3b60; color: #ffffff; font-size: 13px; font-weight: 600;">{{TEXTE}}</span>
```
