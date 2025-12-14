Lab2 : Code Source management


# Étape 1 : Initialiser le dépôt Git

## Objectif
Initialiser un dépôt Git local pour le projet **mlops-lab-01** et configurer les fichiers à ignorer.

---

## 1. Accéder au dossier du projet


cd mlops-lab-01

Initialiser le dépôt Git

<img width="413" height="128" alt="img1_lab2" src="https://github.com/user-attachments/assets/6ec154a2-4bd7-4b36-ab51-4a57ebe61fb8" />

Afficher les fichiers et dossiers cachés

<img width="584" height="279" alt="img2_lab2" src="https://github.com/user-attachments/assets/ce3b894a-bb87-457f-832a-31782d4fbc8f" />



Créer le fichier .gitignore

Créer un fichier .gitignore à la racine du projet et ajouter le contenu suivant :

<img width="195" height="134" alt="img3_lab2" src="https://github.com/user-attachments/assets/d5575d88-f6d6-49d9-a09d-552076088633" />

<img width="272" height="41" alt="img25_lab2" src="https://github.com/user-attachments/assets/52312ec9-f762-44c9-b109-a69b82862722" />

# Étape 2 : Premier commit du projet MLOps

## Objectif
Créer le **premier commit Git** du projet afin de versionner la structure
initiale du lab MLOps (code, données et registry).

---

## 1. Ajouter les fichiers et dossiers principaux

Ajouter au staging :
- le dossier `src/` (code Python),
- le dossier `data/` (données),
- le dossier `registry/` (métadonnées & registry),
- le fichier `.gitignore`.


git add src data registry .gitignore

<img width="394" height="46" alt="img26_lab2" src="https://github.com/user-attachments/assets/5bc0bbcc-8ad4-4b84-a93c-668641553c83" />

Créer le premier commit et on Vérifie l’historique Git

<img width="530" height="173" alt="img6_lab2" src="https://github.com/user-attachments/assets/2f78dff1-8b2a-46d1-aca6-2a641bea911b" />

# Étape 3 : Observer une modification avec `git diff`

## Objectif
Comprendre comment **visualiser les changements** dans le code avant
de les valider, en utilisant `git diff` et `git diff --staged`.

---

## 1. Modifier un fichier existant

Ouvrir le fichier suivant :

src/monitor_drift.py



Modifier une valeur du code, par exemple le seuil de détection du drift :


z_threshold = 2.5  # valeur originale

devient :

z_threshold = 2.0

<img width="419" height="169" alt="img7_lab2" src="https://github.com/user-attachments/assets/b35a9215-955f-4716-8f5d-c06afe2c808b" />

puis on Ajoute le fichier modifié à l’index (staging) et on Observe les différences en staging

<img width="436" height="181" alt="img8_lab2" src="https://github.com/user-attachments/assets/adb9d6a5-dbf0-4805-9e3e-8b03bea48468" />


On Crée un commit de la modification

<img width="546" height="61" alt="img27_lab" src="https://github.com/user-attachments/assets/12070e2b-a0a7-4f8e-9544-19d8797117ca" />

# Étape 4 : Créer une branche de fonctionnalité

## Objectif
Isoler le développement d’une nouvelle fonctionnalité dans une **branche dédiée**,
sans impacter directement la branche principale du projet.

---

## 1. Créer une branche de fonctionnalité

Créer et basculer vers une nouvelle branche :


git checkout -b feature/api-request-id puis Modifie le code dans la branche Ajouter une petite logique liée au request_id, par exemple :

génération automatique d’un request_id si non fourni, amélioration du traçage des requêtes, puis on Ajoute et valider les modifications et on Créer le commit correspondant et on Vérifie les branches existantes

<img width="491" height="119" alt="img28_lab2" src="https://github.com/user-attachments/assets/0bbdf523-cbd5-4d21-926b-00f40a6d65bd" />


# Étape 5 : Fusionner une branche de fonctionnalité

## Objectif
Intégrer une **branche de fonctionnalité** dans la branche principale
après validation du code.

---

## 1. Se placer sur la branche principale

Basculer vers la branche principale du projet (`main` ou `master`) :


git switch master (mon cas)
# ou
git switch main

<img width="383" height="71" alt="img10_lab2" src="https://github.com/user-attachments/assets/c836b3ef-3b44-42d9-b34c-1286c32dbed4" />

on Vérifie l’historique des commits

<img width="504" height="137" alt="img11_lab2" src="https://github.com/user-attachments/assets/df757b96-3a87-4e87-9d05-ce5bd3490f53" />


# Étape 6 : Créer et résoudre un conflit de merge

## Objectif
Simuler un **conflit Git réel** en modifiant la même partie du code
dans deux branches différentes, puis apprendre à le **résoudre proprement**.

---

## 1. Créer une nouvelle branche de fonctionnalité

Créer et basculer vers une nouvelle branche :


git checkout -b feature/change-gate
et puis Modifier la valeur par défaut de gate_f1 :

gate_f1 = 0.60

<img width="487" height="132" alt="img12_lab2" src="https://github.com/user-attachments/assets/2cff84d0-93b4-4a68-9fb2-0b7315d9f998" />

On Ajoute et committe la modification :

<img width="493" height="90" alt="img13_lab2" src="https://github.com/user-attachments/assets/22b177c2-3386-46cf-8f40-d95052a6071f" />

Modifier à nouveau src/train.py avec une valeur différente :

<img width="488" height="101" alt="img14_lab" src="https://github.com/user-attachments/assets/0dbc0fb9-a7ff-4ec5-aa44-e4fda78a247e" />

<img width="494" height="142" alt="img15_lab2" src="https://github.com/user-attachments/assets/6c6c2e84-a54f-4082-a301-357e4bf2263c" />

Résoudre le conflit dans src/train.py (choisir une valeur, par exemple 0.70), puis

<img width="521" height="89" alt="img16_lab2" src="https://github.com/user-attachments/assets/5c839de6-f31c-4f47-a037-10b3612e92ea" />

# Étape 7 : Utiliser `git stash` dans le contexte du lab MLOps

## Objectif
Apprendre à **mettre temporairement de côté des modifications**
sans créer de commit, afin de pouvoir changer de branche ou continuer
le travail proprement.

---

## 1. Modifier un fichier sans vouloir committer

Apporter une modification non finalisée, par exemple dans `src/rollback.py` :


# TODO: improve rollback safety checks

<img width="548" height="91" alt="img17_lab2" src="https://github.com/user-attachments/assets/e7f127bc-303e-4a04-a4df-63c6544032df" />

On Vérifie l’état du dépôt et on Met de côté les modifications avec git stash puis on Liste les stash existants on Applique le dernier stash sans le supprimer enfin on Restaure les modifications et supprimer le stash

<img width="598" height="433" alt="img18_lab2" src="https://github.com/user-attachments/assets/3e22f2f1-d850-4ff6-b0d4-b08151a8f6d3" />


# Étape 8 : Tester `git reset` sur un fichier d’expérimentation

## Objectif
Comprendre les différences entre **`git reset --soft`**, **`git reset` (mixed)**  
et **`git reset --hard`** à travers un exemple simple et contrôlé.

---

## 1. Créer un dossier d’expérimentation

Créer un dossier dédié aux tests Git :


mkdir experiments

puis on Crée un fichier de test (version v1)
et on Modifie et committe la version v2
puis on Modifie et committe la version v3
ensuite on Teste git reset --soft

<img width="528" height="438" alt="img19_lab2" src="https://github.com/user-attachments/assets/29c2b540-b810-4a09-85bf-175537ec6052" />

<img width="400" height="429" alt="img20_lab2" src="https://github.com/user-attachments/assets/2e7fec8d-9768-46f5-bb38-a5ef253a4cc8" />

# Étape 9 : Annuler un commit avec `git revert`

## Objectif
Comprendre l’utilisation de **`git revert`** pour annuler un commit **sans réécrire l’historique**,  
ce qui est la méthode recommandée en **environnement collaboratif ou en production**.

Contrairement à `git reset`, `git revert` crée **un nouveau commit inverse**.

---

## 1. Ajouter un changement non souhaité

Ajouter volontairement une mauvaise modification dans `src/api.py` :


echo "# BAD CHANGE" >> src/api.py
git add src/api.py
git commit -m "feat(api): add bad change"

puis on Vérifie l’historique des commits
et on Annule le commit avec git revert

<img width="419" height="259" alt="img21_lab2" src="https://github.com/user-attachments/assets/4797b891-95df-4aea-a75d-c53267f46b26" />

On Vérifie le contenu du fichier

<img width="487" height="437" alt="img22_lab2" src="https://github.com/user-attachments/assets/0b95b080-3f71-419d-bc01-8786da059c5c" />

# Étape 10 : Rebase d’une branche feature sur la branche principale

## Objectif
Comprendre l’utilisation de **`git rebase`** pour rejouer les commits d’une branche
de fonctionnalité **au-dessus de la branche principale**, afin d’obtenir
un historique **linéaire et propre**.

Cette pratique est courante avant l’intégration finale d’une feature en MLOps.

---

## 1. Créer une branche de fonctionnalité

Créer et basculer sur une nouvelle branche :


git checkout -b feature/drift-last-n

On Modifie src/monitor_drift.py en changeant la valeur de last_n
(par exemple de 200 à 500)
On Ajoute et créer un commit 
On Crée un nouveau commit sur la branche principale
On Revient sur la branche feature

On Rebase la branche feature sur la branche principale
On Vérifie l’historique Git

<img width="553" height="412" alt="img24_lab2" src="https://github.com/user-attachments/assets/4116cf12-0135-4d41-906f-c0224d9489d8" />
