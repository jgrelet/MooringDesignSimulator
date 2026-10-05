# Mooring Design Simulator — Installation et premier lancement

[English version](INSTALLATION.md).

## Contenu de l'archive

L'archive de livraison contient généralement :

- l'application MooringDesignSimulator ;
- le dossier `library`, avec la bibliothèque de composants Excel ;
- le dossier `examples`, avec des projets d'exemple ;
- ce fichier `INSTALLATION.md` ;
- le fichier `CHANGELOG.md`.

## Installation

1. Téléchargez l'archive correspondant à votre système.
2. Décompressez toute l'archive dans un dossier de votre choix.
3. Conservez ensemble l'application, le dossier `library` et le dossier `examples`.
4. Lancez l'application depuis le dossier décompressé.

Notes par système :

- Windows : lancez `mooringDesignSimulator.exe`.
- macOS : lancez `mooringDesignSimulator.app`. Au premier lancement, si macOS bloque l'application car elle provient d'Internet, utilisez clic droit puis `Open` / `Ouvrir`, puis confirmez l'ouverture.
- Linux : lancez `mooringDesignSimulator`. Si nécessaire, rendez le fichier exécutable avec `chmod +x mooringDesignSimulator`.

Important :

- ne séparez pas l'application des dossiers `library` et `examples` ;
- ne renommez pas la bibliothèque par défaut sans mettre à jour son chemin dans le logiciel ;
- évitez d'exécuter l'application directement depuis une archive non décompressée.

## Mise à jour depuis une version antérieure

Si vous mettez à jour Mooring Design Simulator alors qu'un projet utilise déjà une bibliothèque chargée (par exemple depuis v2.0.12 ou avant) :

1. remplacez le dossier `library` de l'installation par celui de la nouvelle archive, ou chargez le nouveau `library/Library-v2.xls` ;
2. dans le menu `Library`, utilisez **Reload current library** pour recharger le catalogue Excel.

Cette étape est nécessaire pour afficher les **nouveaux terminaux** (manilles, anneau galvanisé, grillette Dyneema) et appliquer leurs **caractéristiques mises à jour** dans la palette et les projets ouverts.

## Premier lancement

Au premier démarrage, le logiciel crée automatiquement :

- un fichier de configuration utilisateur ;
- une base de données locale pour le projet de travail temporaire ;
- un cache SQLite local de la bibliothèque.

Ces fichiers sont créés dans le dossier de configuration utilisateur du système.

## Première utilisation

1. Charger la bibliothèque
   - Menu `Library`
   - si besoin, utiliser `Load new library`
   - la bibliothèque par défaut est `library/Library-v2.xls`

2. Ouvrir ou créer un projet
   - Menu `File > Open mooring` pour ouvrir un projet existant
   - ou `File > New mooring` pour commencer un nouveau mouillage

3. Tester avec un exemple
   - ouvrir `examples/test-1.mooring.sqlite3` pour un projet V2 pret a l'emploi
   - ou importer un projet de la V1 originale : `examples/mouillage_luckyscale_2021/luckyscale_2021_dyneema.py` ou `examples/mouillage_microrio_2021_ATALANTE/MICROMOORING2021_atalante.py`

4. Construire ou modifier la ligne de mouillage
   - sélectionner un composant dans la bibliothèque
   - cliquer sur `Add selected` ou utiliser le glisser-déposer
   - utiliser le sélecteur `After | Before` dans la barre du concepteur
   - le mode par défaut est `After`
   - ce mode s'applique de façon cohérente au glisser-déposer et aux insertions liées au segment sélectionné
   - utiliser le clic droit sur un segment pour afficher le menu contextuel

5. Régler l'environnement
   - Menu `Configuration > Set environmental conditions`
   - définir ou importer un profil de courant

6. Lancer une simulation
   - Menu `Simulate > Start simulation`
   - consulter ensuite les onglets de résultats dans `Simulation`

7. Consulter l'aide intégrée
   - Menu `Help > Help Content`
   - une aide locale résumant les principales fonctionnalités est fournie dans le logiciel

8. Générer un rapport
   - Menu `Report > Generate report`

## Bibliothèque de composants

La bibliothèque de composants est lue depuis un fichier Excel.

Si vous modifiez le fichier Excel :

1. enregistrez le fichier ;
2. revenez dans le logiciel ;
3. utilisez `Reload current library`.

Certaines colonnes booléennes du fichier Excel sont importantes pour le clampage :

- `supports_clamp` : indique si un support peut recevoir un instrument clampé ;
- `is_clampable` : indique si un composant peut être clampé sur un support.

Ces valeurs doivent être adaptées à votre contexte d'utilisation.

Sur l'onglet **Anchors**, la colonne **Mass (kg, dry)** contient la masse mesurée dans l'air pour les lests types (par exemple **Concrete ballast cylinder 1 m**). Laissez-la vide pour un lest dont la masse sera calculée automatiquement par la simulation (solveur). La colonne **Density (kg/m³)** contient la densité du matériau utilisée pour convertir cette masse en masse immergée. L'application affiche ensuite cette masse immergée estimée dans les résultats de simulation.

Pour mettre à jour la feuille **Anchors** du fichier livré : `python tools/update_library_anchors.py`.

Guide détaillé des colonnes Excel (formules, aires projetées, masses, coefficients) :
[docs/component-library-excel.md](https://github.com/jgrelet/MooringDesignSimulator/wiki/Component-library-fr).

## Formats de fichiers

- Projet principal V2 : `.mooring.sqlite3`
- Export lisible : `.json`
- Projet historique V1 : `.py`
- Bibliothèque : `.xls`
- Profils de courant : `.csv`, `.txt`, `.nc` / NetCDF
