<div align="center">

<img src="docs/icone.png" alt="Icône BTP Compagnon" width="120" />

# BTP Compagnon

**Le rappel des bonnes pratiques du bâtiment, dans la poche.**

![Android](https://img.shields.io/badge/Android-8.0%2B-3DDC84?logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-1.9-7F52FF?logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-Material%203-4285F4?logo=jetpackcompose&logoColor=white)
![Hors ligne](https://img.shields.io/badge/100%25-hors%20ligne-455A64)

</div>

Application Android (Kotlin + Jetpack Compose) qui regroupe des **fiches de rappel** pour les métiers du bâtiment :
élingage, échafaudage, tour d'étaiement, conduite d'engins, habilitation électrique, gros œuvre, second œuvre, dosages, santé et sécurité…

Pas de quiz, pas de compte, pas de connexion : on ouvre une fiche, on relit les consignes (avant, pendant, après, vérifications, interdits, urgences) et on retourne au travail.

> [!IMPORTANT]
> **Ce projet n'est pas un document officiel et n'est affilié à aucun organisme de formation (AFPA, INRS, OPPBTP…).**
> Le contenu est un **rappel général** rédigé à partir du Code du travail, des recommandations de prévention (INRS, CNAM/CARSAT, OPPBTP) et des normes usuelles. Il n'a **pas été validé par des formateurs** : à faire relire avant toute utilisation en formation.
> Il ne remplace ni la formation, ni la notice du fabricant, ni les consignes de l'employeur, ni la réglementation en vigueur (fréquences de vérification, dosages et valeurs peuvent évoluer ou varier selon le chantier).

## Aperçu

<div align="center">
<img src="docs/schema-elingage-angles.png" alt="Schéma : angles d'élingage" width="31%" />
<img src="docs/schema-echafaudage.png" alt="Schéma : échafaudage de pied" width="31%" />
<img src="docs/schema-dosage-beton.png" alt="Schéma : dosage du béton" width="31%" />
</div>

## Fonctionnalités

- **66 fiches** réparties en **11 domaines**, avec une trame commune : avant, pendant, après, vérifications, interdits, en cas d'incident
- **62 schémas vectoriels originaux** (aucune photo) en haut des fiches : angles et modes d'élingage, crochet et linguet, échafaudages, tranchée, dosage du béton…
- **Recherche** insensible aux accents
- **Favoris** mémorisés sur le téléphone
- **Partage** d'une fiche en texte
- **Numéros d'urgence** avec appel direct (15, 18, 17, 112, urgence gaz, 114 par SMS)
- **Thème clair et sombre**, fonctionnement **100 % hors ligne**

## Contenu

| Domaine | Fiches | Exemples |
|---|:-:|---|
| Levage & élingage | 7 | élingage, accessoires, grue à tour, grue mobile, pont roulant, nacelle |
| Hauteur, échafaudage & étaiement | 7 | échafaudage de pied et roulant, tour d'étaiement, échelles, antichute |
| Conduite d'engins | 8 | pelle, chargeuse, tombereau, compacteur, chariots, CACES |
| Habilitation électrique | 6 | titres, B0/H0, consignation, chantier, réseaux, accident |
| Gros œuvre | 8 | dosage béton, dosage mortier et chape, coffrage, ferraillage, bétonnage, démolition |
| Second œuvre | 8 | plâtre et colles, peinture, résines bi-composants, menuiserie, isolation |
| Couverture & charpente | 3 | travaux en toiture, charpente |
| Plomberie & chauffage | 3 | plomberie sanitaire, gaz |
| Santé & sécurité | 9 | EPI, bruit, poussières, incendie, secours, chaleur et froid, espaces confinés, chimie |
| Soudage & métallerie | 3 | soudage à l'arc, meulage, bouteilles de gaz |
| Organisation & règles d'or | 4 | règles d'or, PGC et PPSPS, vérifications périodiques, droit de retrait |

## À propos

Un écran « À propos » (accessible en bas de l'accueil) présente l'auteur, la version et le lien vers ce dépôt : [github.com/Renaf2/BTP-Compagnon](https://github.com/Renaf2/BTP-Compagnon).
L'image de profil est `app/src/main/res/drawable-nodpi/profil.jpg`.

## Installation

**Prérequis :** Android Studio récent (Koala ou plus), JDK 17 (fourni avec Android Studio), un téléphone ou un émulateur Android 8.0 (API 26) minimum.

```bash
git clone https://github.com/Renaf2/BTP-Compagnon.git
cd BTPCompagnon
```

1. Ouvrir Android Studio, puis **File > Open** et choisir le dossier `BTPCompagnon`.
2. Attendre la synchronisation Gradle (connexion Internet nécessaire la première fois). Accepter l'installation du SDK Android 34 si Android Studio la propose.
3. Choisir un appareil et lancer avec **Run ▶**.

En ligne de commande : `./gradlew assembleDebug` produit l'APK dans `app/build/outputs/apk/debug/`.

## Structure du projet

```
app/src/main/
├── assets/illustrations.json        # les schémas (formes vectorielles simples)
├── java/com/btpformation/app/
│   ├── MainActivity.kt
│   ├── data/
│   │   ├── Models.kt                # Fiche, Section, Categorie + helpers (avant, pendant, verifs…)
│   │   ├── Content1.kt … Content4.kt  # tout le contenu des fiches
│   │   ├── Catalogue.kt             # catégories, recherche, favoris
│   │   └── Illustrations.kt         # lecture du JSON des schémas
│   └── ui/
│       ├── Screens.kt               # accueil, catégorie, fiche, favoris, urgences
│       ├── IllustrationView.kt      # dessin des schémas sur Canvas
│       └── theme/Theme.kt
└── res/                             # icône adaptative, thèmes, chaînes
```

- **Technique :** Kotlin 1.9, Jetpack Compose (Material 3), AGP 8.5, Gradle 8.7, `minSdk` 26, `targetSdk` 34. Navigation sans bibliothèque externe, favoris dans `SharedPreferences`.
- L'identifiant technique de l'application est `com.btpformation.app` (non visible par l'utilisateur).

## Contribuer au contenu

### Ajouter ou modifier une fiche

Tout le contenu est dans `app/src/main/java/com/btpformation/app/data/Content1.kt` à `Content4.kt`. Une fiche se déclare ainsi :

```kotlin
Fiche(
    id = "ma-fiche",
    titre = "Titre de la fiche",
    resume = "Une phrase de résumé.",
    sections = listOf(
        avant("Vérifier ceci.", "Contrôler cela."),
        pendant("Faire ceci."),
        verifs("Point de contrôle."),
        interdits("À ne jamais faire."),
        urgence("Que faire en cas d'incident.")
    ),
    reference = "Texte de référence (norme, article du Code du travail)."
)
```

Pour ajouter un domaine, créer un objet `Categorie` et l'ajouter à la liste dans `Catalogue.kt`.

### Ajouter un schéma

Les schémas sont décrits dans `app/src/main/assets/illustrations.json` : un identifiant, un titre, une légende, la liste des fiches concernées (`"fiches"`), une taille et une liste de formes (`l` ligne, `r` rectangle, `c` cercle, `p` polygone, `t` texte ; couleurs en `#RRGGBB`, chaîne vide pour « aucune »). Il suffit d'ajouter l'identifiant d'une fiche dans `"fiches"` pour associer un schéma existant à une autre fiche.

### Relecture

Les relectures par des formateurs, conducteurs de travaux ou préventeurs sont particulièrement utiles : signaler toute valeur ou consigne inexacte via une *issue* ou une *pull request*. Merci de citer la source (article du Code du travail, norme, recommandation INRS/OPPBTP, notice fabricant).

## Limites connues

- Le contenu est volontairement synthétique : une fiche rappelle l'essentiel, elle ne remplace pas la formation.
- Les valeurs chiffrées (fréquences de vérification, dosages, distances) sont des **ordres de grandeur** ; le plan, le CCTP, le DTU ou la notice du fabricant priment.
- Les schémas sont **indicatifs** : ils illustrent un principe, pas une configuration exacte.

## Licence

À définir par le dépôt (par exemple MIT pour le code et CC BY-SA pour le contenu). Tant qu'aucune licence n'est ajoutée, tous droits réservés.
