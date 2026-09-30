# Planning-rh

## Description

Application console développée en Java permettant d'administrer une équipe de salariés et de planifier leurs heures de travail dans le respect strict des contrats (temps plein, temps partiel) et des quotas légaux. Le système agit comme un garde-fou RH en bloquant toute saisie non conforme ou en dépassement de plafond.

---

## 💡 Vision du Projet

* **Respect strict de l'encapsulation** : protection totale du compteur d'heures (`heuresEffectuees`). Aucun accès direct ni modification arbitraire ; chaque ajout passe par un sas de validation métier.

* **Architecture orientée objet robuste** : utilisation de l'héritage et du polymorphisme via une classe abstraite `Employe` et des contrats spécialisés (`TempsPlein`, `TempsPartiel`) appliquant dynamiquement leurs propres règles de plafond.

* **Zéro dépendance externe** : développement en Java pur standard (JDK standard) sans framework lourd, exécutable directement en ligne de commande.

---

## 🎯 Fonctionnalités principales

1. **Enregistrer un employé** : création d'un salarié avec son identifiant, son nom, son prénom, son taux horaire et son type de contrat.

2. **Ajouter un shift d'heures** : saisie du nombre d'heures effectuées avec rejet automatique des valeurs négatives et des dépassements de quota contractuel.

3. **Consulter l'état de l'équipe** : affichage du récapitulatif des heures effectuées, des heures restantes disponibles et du statut de conformité.

4. **Clôturer et réinitialiser la semaine** : remise à zéro contrôlée des compteurs d'heures pour basculer sur un nouveau cycle de planning.

---

## 🛠️ Stack Technique

- **Langage** : Java

- **Paradigme** : Programmation orientée objet (encapsulation, abstraction, polymorphisme)

- **Environnement** : Linux / WSL (Ubuntu)

- **Interface** : Console interactive (CLI / Terminal)

- **Versionnement** : Git & GitHub

---

## 📂 Architecture du Projet

```text
planning-rh/
│
├── .gitignore          # Fichiers exclus du versionnement (*.class, bin/)
├── README.md           # Documentation du projet
├── bin/                # Bytecode compilé (.class)
└── src/                # Code source Java
    ├── Employe.java       # Classe mère abstraite (état, sas de validation)
    ├── TempsPlein.java    # Spécialisation temps plein (plafond 35 h)
    ├── TempsPartiel.java  # Spécialisation temps partiel (plafond 24 h)
    ├── GestionRH.java     # Moteur de gestion de la liste des salariés
    └── Main.java          # Point d'entrée et scénarios de simulation
```

---

## 🖥️ Aperçu de l'Expérience Utilisateur

```text
=== Planning-RH ===
1. Ajouter un employé
2. Enregistrer des heures (shift)
3. Afficher le planning de la semaine
4. Réinitialiser la semaine
5. Quitter

--- Enregistrement d'un shift ---
ID de l'employé : EMP-02 (Bob - Temps partiel, max 24.0h)
Heures actuelles : 20.0h
Nombre d'heures à ajouter : 6.0

❌ Erreur : Ajout refusé. 
Le total (26.0h) dépasse le plafond autorisé de 24.0h pour ce contrat.
Compteur inchangé : 20.0h
```

---

## 🚀 Lancement Rapide

1. Cloner le projet sur votre machine

2. Compiler le projet :
     ```bash
        javac -d bin src/*.java     
    ```
3. Lancer l'application :
     ```bash
    java -cp bin Main
    ```