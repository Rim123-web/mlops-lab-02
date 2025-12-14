Lab2 : Code Source management


# Étape 1 : Initialiser le dépôt Git

## Objectif
Initialiser un dépôt Git local pour le projet **mlops-lab-01** et configurer les fichiers à ignorer.

---

## 1. Accéder au dossier du projet


cd mlops-lab-01

Initialiser le dépôt Git

<img width="413" height="128" alt="img1_lab2" src="https://github.com/user-attachments/assets/ef41e204-61e3-4be6-8c0a-0679fa35f383" />

Afficher les fichiers et dossiers cachés

<img width="584" height="279" alt="img2_lab2" src="https://github.com/user-attachments/assets/1a6273d7-a652-4ca2-acd1-e82a639c1a01" />


Créer le fichier .gitignore

Créer un fichier .gitignore à la racine du projet et ajouter le contenu suivant :

<img width="195" height="134" alt="img3_lab2" src="https://github.com/user-attachments/assets/16f0f901-e0b2-4f15-aece-c7138501d7ed" />

<img width="272" height="41" alt="img25_lab2" src="https://github.com/user-attachments/assets/7f4d8eea-0187-41c8-9713-4f23fb8894ee" />

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

<img width="394" height="46" alt="img26_lab2" src="https://github.com/user-attachments/assets/13e36741-892d-49dd-89c1-ede911100d63" />

Créer le premier commit et on Vérifie l’historique Git

<img width="530" height="173" alt="img6_lab2" src="https://github.com/user-attachments/assets/f7576838-0995-477a-a791-4f5eb8ce1a47" />

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

<img width="419" height="169" alt="img7_lab2" src="https://github.com/user-attachments/assets/4c7c9081-35dd-49cb-9eb8-43704d4e81bb" />

puis on Ajoute le fichier modifié à l’index (staging) et on Observe les différences en staging
<img width="436" height="181" alt="img8_lab2" src="https://github.com/user-attachments/assets/57de4834-a629-418c-a6f1-83a18ea40326" />

On Crée un commit de la modification

<img width="546" height="61" alt="img27_lab" src="https://github.com/user-attachments/assets/56554ce6-180c-49c2-98bb-92ba3b7ca4fd" />

# Étape 4 : Créer une branche de fonctionnalité

## Objectif
Isoler le développement d’une nouvelle fonctionnalité dans une **branche dédiée**,
sans impacter directement la branche principale du projet.

---

## 1. Créer une branche de fonctionnalité

Créer et basculer vers une nouvelle branche :


git checkout -b feature/api-request-id puis Modifie le code dans la branche Ajouter une petite logique liée au request_id, par exemple :

génération automatique d’un request_id si non fourni, amélioration du traçage des requêtes, puis on Ajoute et valider les modifications et on Créer le commit correspondant et on Vérifie les branches existantes

<img width="491" height="119" alt="img28_lab2" src="https://github.com/user-attachments/assets/907c5f56-89fb-4f52-966c-31e3fb338964" />


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

<img width="383" height="71" alt="img10_lab2" src="https://github.com/user-attachments/assets/cb1d0afc-99a5-45c5-bd64-2ac474e06b29" />

on Vérifie l’historique des commits

<img width="504" height="137" alt="img11_lab2" src="https://github.com/user-attachments/assets/bc948621-4251-4a4e-b194-a7adc31f4b26" />


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

<img width="487" height="132" alt="img12_lab2" src="https://github.com/user-attachments/assets/2c935395-5148-47cc-8e9d-64f3f2411d23" />

On Ajoute et committe la modification :

<img width="493" height="90" alt="img13_lab2" src="https://github.com/user-attachments/assets/11f08cf0-02da-486f-9334-1d5b5c795e4d" />

Modifier à nouveau src/train.py avec une valeur différente :

<img width="488" height="101" alt="img14_lab" src="https://github.com/user-attachments/assets/67ccc5be-7e94-49fb-9d7a-c58c1eacb0b1" />
<img width="494" height="142" alt="img15_lab2" src="https://github.com/user-attachments/assets/7bc003c4-d197-4d91-bf5e-50b25c72a92d" />

Résoudre le conflit dans src/train.py (choisir une valeur, par exemple 0.70), puis

<img width="521" height="89" alt="img16_lab2" src="https://github.com/user-attachments/assets/219f2598-39b4-4d0e-81a7-044412a4f6df" />

# Étape 7 : Utiliser `git stash` dans le contexte du lab MLOps

## Objectif
Apprendre à **mettre temporairement de côté des modifications**
sans créer de commit, afin de pouvoir changer de branche ou continuer
le travail proprement.

---

## 1. Modifier un fichier sans vouloir committer

Apporter une modification non finalisée, par exemple dans `src/rollback.py` :


# TODO: improve rollback safety checks

<img width="548" height="91" alt="img17_lab2" src="https://github.com/user-attachments/assets/2e6f858b-0e4a-4513-aec1-f6b7cfd9e1ed" />

On Vérifie l’état du dépôt et on Met de côté les modifications avec git stash puis on Liste les stash existants on Applique le dernier stash sans le supprimer enfin on Restaure les modifications et supprimer le stash

<img width="598" height="433" alt="img18_lab2" src="https://github.com/user-attachments/assets/8470a5b6-bff0-4b32-97bd-02d9fc5e7c88" />


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

<img width="528" height="438" alt="img19_lab2" src="https://github.com/user-attachments/assets/8bb909cd-e890-4108-8981-b6187dbcc177" />

<img width="400" height="429" alt="img20_lab2" src="https://github.com/user-attachments/assets/3a66ba2a-82c1-45dc-a9a8-c596c6f031c1" />

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

<img width="419" height="259" alt="img21_lab2" src="https://github.com/user-attachments/assets/fe3ee81f-0d10-429e-a0e5-77179f360805" />

On Vérifie le contenu du fichier

<img width="487" height="437" alt="img22_lab2" src="https://github.com/user-attachments/assets/cdfadb66-9943-4271-8e3b-1423f7539d59" />

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

<img width="553" height="412" alt="img24_lab2" src="https://github.com/user-attachments/assets/53072c2d-d68a-408a-869c-ad162b3db157" />
