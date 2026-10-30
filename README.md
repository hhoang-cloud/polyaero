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
