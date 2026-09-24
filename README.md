# Forge FP Calculator — interface revisitée

Le projet Android Studio complet se trouve dans [`ForgeFPCalculator/`](ForgeFPCalculator/). L'APK de release est disponible à la racine : [`ForgeFPCalculator-1.0.0-release-v2.apk`](ForgeFPCalculator-1.0.0-release-v2.apk).

## Ce qui a changé

- Nouvelle identité visuelle ardoise, turquoise et or, avec l'illustration **du bâtiment réellement sélectionné**.
- Parcours plus clair : préparation du niveau → résultat → emplacements → ordre de pose.
- Affichage adapté au téléphone (vue rapide des cinq places, cartes lisibles) et à la tablette (tableau complet, panneaux en colonnes).
- Sélecteurs de bâtiment/niveau, bibliothèque de documents et états vides harmonisés.
- Formule explicative synchronisée avec le multiplicateur choisi ; boutons de copie et de partage conservés.
- Lecture `.xlsx` fiabilisée : lignes vides/cachées alignées avec les images, couleurs de thème/indexées, fonds `fgColor`/`bgColor` et principales mises en forme conditionnelles (dont dégradés et texte contenu).
- **Zoom/dézoom complet des documents** (PDF et Excel) : boutons `+`/`−`, pincement à deux doigts, et toucher le pourcentage pour revenir à 100 %.

La structure Android, le catalogue local, le lecteur PDF et la formule de calcul sont conservés. Des tests de non-régression ciblent désormais le lecteur Excel.

## Zoom des documents (PDF et Excel)

Les deux visionneuses partagent la même fonction de zoom :

- Boutons `+` / `−` dans la barre d'outils, avec affichage du pourcentage courant.
- **Pincement à deux doigts** sur la page PDF ou la feuille de calcul ; seul le geste à deux doigts est intercepté, le défilement à un doigt reste fluide.
- Toucher le pourcentage remet le zoom à 100 %.
- Plage PDF : 50 % → 300 %. Plage tableur : 60 % → 240 %.

## Ouvrir et vérifier

Avec **JDK 17+** et **Android SDK 35**, ouvrez `ForgeFPCalculator/` dans Android Studio, ou exécutez :

```bash
cd ForgeFPCalculator
./gradlew test
./gradlew assembleDebug
```

La clé de signature de l'archive d'origine n'est pas dupliquée dans les sources suivies séparément. Pour une publication depuis le dossier source, fournissez votre propre clé de signature. Le débogage et les tests n'en ont pas besoin.
