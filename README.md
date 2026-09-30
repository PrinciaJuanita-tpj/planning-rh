# planning-rh

## Description

Mini-logiciel console de gestion du personnel et de suivi des heures de travail, conçu pour faire respecter les quotas légaux et contractuels (restauration, commerce).

---

## Objectifs du projet

- Modéliser une organisation d'équipe avec différents types de contrats.
- Mettre en œuvre les principes fondamentaux de la programmation orientée objet :
  - **Encapsulation :** protection stricte de l'état interne des salariés (compteur d'heures) et validation des saisies.
  - **Héritage :** factorisation des attributs et comportements communs via une classe de base.
  - **Polymorphisme :** application de plafonds horaires dynamiques selon le type de contrat.

---

## Règles Métiers

- **Types de contrats :**
  - **Temps plein :** plafonné à 35 h / semaine.
  - **Temps partiel :** plafonné à 24 h / semaine (ou quota contractuel défini).
- **Contrôle des heures (`ajouterHeures`) :**
  - Rejet de toute valeur négative ou nulle.
  - Rejet de tout ajout entraînant un dépassement du plafond hebdomadaire de l'employé.
- **Cycle hebdomadaire :** possibilité de réinitialiser le compteur à zéro pour une nouvelle semaine.

---

## Structure du Projet

```text
planning-rh/
├── bin/                 # Fichiers compilés (.class)
├── src/                 # Code source Java (.java)
│   ├── Employe.java       # Classe abstraite de base
│   ├── TempsPlein.java    # Salarié à temps plein (plafond 35 h)
│   ├── TempsPartiel.java  # Salarié à temps partiel (plafond 24 h)
│   ├── GestionRH.java     # Administration de l'équipe et planning
│   └── Main.java          # Point d'entrée et scénarios de test
└── README.md
```