# Guide Réglementaire, Technique et Complémentaire : Gestion de la Paie au Maroc (Version Robustesse)
### Spécifications Avancées pour le Développement d'un Moteur de Paie Certifiable (Payroll Engine v2)

Ce document complète le cadre de base en apportant les références juridiques, fiscales et techniques indispensables pour gérer les cas limites (edge cases), les contrats spéciaux, les obligations déclaratives électroniques (EDI) et sécuriser l'application contre les risques de redressement lors des audits.

---

## 1. Les Formats Techniques de Déclaration Électronique (EDI)
Une application moderne ne doit pas simplement imprimer des PDF ; elle doit générer des fichiers structurés conformes aux cahiers des charges des administrations marocaines.

| Administration | Document / Référence Technique | Utilité Fonctionnelle pour l'Application |
| :--- | :--- | :--- |
| **DGI (Direction Générale des Impôts)** | **Cahier des charges de la Déclaration Annuelle des Salaires (État 9421 / Simpl-IR)** <br>*Mis à jour périodiquement selon les formats XML de la DGI.* | **Module de Clôture Annuelle :** <br>Spécifie la structure exacte du fichier XML (balises, types de données, contrôles de cohérence) que l'employeur doit téléverser chaque année avant le 1er mars pour déclarer l'IR, les indemnités exonérées et les avantages accordés à chaque salarié. |
| **CNSS (Caisse Nationale de Sécurité Sociale)** | **Guide de Formatage des Fichiers de Déclaration de Salaires (Damancom)** <br>*Spécifications des fichiers plats (.txt ou .csv).* | **Module Mensuel CNSS :** <br>Définit la structure des fichiers de déclaration des salariés (numéro d'immatriculation, nom, jours ouvrés, salaire brut cotisable). Votre application doit générer ce fichier pour éviter la saisie manuelle au client. |

---

## 2. Abattements Spéciaux et Frais Professionnels Majorés (Fiscalité Avancée)
Le taux standard de déduction des frais professionnels (pour passer du Salaire Brut Imposable au Salaire Net Imposable) est soumis à un plafond général. Cependant, le Code Général des Impôts (CGI) prévoit des **taux majorés** pour certaines professions. Votre application doit intégrer un champ "Catégorie Professionnelle" appliquant ces règles de l'**Article 59-I-A du CGI** :

* **Personnel navigant de la marine marchande et de la pêche maritime :** Taux d'abattement spécifique.
* **Journalistes, rédacteurs, photographes et directeurs de journaux :** Abattement majoré (généralement 35%).
* **Voyageurs, Représentants et Placiers (VRP) :** Abattement de 45%.
* **Ouvriers mineurs :** Abattement de 35%.
* *Architecture logicielle :* Créez une table de correspondance `Categorie_Professionnelle -> Taux_Abattement -> Plafond_Mensuel` pour rendre le moteur flexible.

---

## 3. Gestion des Contrats Spéciaux : Le Régime ANAPEC
Pour être adoptée par les cabinets de comptabilité et les départements RH, l'application doit gérer nativement les contrats d'insertion de l'ANAPEC.

* **Référence Légale :** *Loi n° 16-04* et dispositions spécifiques du CGI (mises à jour par les Lois de Finances).
* **Règles de calcul à coder :**
    * **Exonération fiscale et sociale :** Non-soumission à l'IR, à la CNSS et à la TFP de la rémunération mensuelle brute (dans la limite des plafonds légaux, historiquement fixés à 6 000 DH, soumis à vérification selon la Loi de Finances en vigueur).
    * **Condition AMO :** La part patronale et salariale de l'Assurance Maladie Obligatoire (AMO) reste due ou bénéficie d'une prise en charge par l'État selon le type exact de programme (Idmaj / Taehil). L'application doit proposer des cases à cocher spécifiques pour ces contrats d'insertion.

---

## 4. Retraites Complémentaires et Prévoyance (Ex: CIMR)
La paie marocaine intègre très souvent des cotisations à des caisses de retraite complémentaire, la principale étant la CIMR (Caisse Interprofessionnelle Marocaine de Retraite).

* **Référence :** *Règlement Général de la CIMR* et *Article 59-II du CGI*.
* **Règles de déductibilité :**
    * Les cotisations salariales aux régimes de retraite complémentaire sont **déductibles du Salaire Brut Imposable** pour le calcul de l'IR, sans limitation de taux si elles respectent les conditions du CGI.
    * Les cotisations patronales sont une charge pour l'entreprise et ne doivent pas être considérées comme un avantage en nature pour le salarié.
    * *Complexité technique :* Gérer les différents taux d'option de la CIMR (choisis par l'entreprise) et la formule de calcul de l'assiette CIMR (souvent basée sur le salaire brut, ou salaire brut moins certaines primes).

---

## 5. La Quotité Saisissable (Saisie sur Salaire)
Si un salarié fait l'objet d'une saisie-arrêt (dette, pension alimentaire), l'application doit calculer automatiquement la part du salaire net qui peut être retenue et celle qui doit obligatoirement lui être laissée pour vivre.

* **Référence Légale :** *Code de Procédure Civile marocain (Dahir du 28 septembre 1974)*, **Articles 488 et suivants**.
* **L'Algorithme des Tranches Saisissables :** Le calcul ne se fait pas sur la totalité du salaire, mais par tranches progressives (le salaire net est divisé en portions dont le pourcentage saisissable augmente avec le revenu, sauf pour les pensions alimentaires où la saisie peut représenter la totalité de la pension due).
    * *Exemple de structure algorithmique :*
        * Jusqu'à une certaine limite : 1/20ème saisissable.
        * Tranche suivante : 1/10ème saisissable, etc.

---

## 6. Règles de Proratisation : Entrées/Sorties et Absences
La robustesse d'un logiciel se mesure à sa capacité à gérer les mois incomplets de manière juste et auditable.

* **La règle du Trentième (1/30) vs Jours Réels :** Le Code du Travail n'impose pas une méthode unique de calcul pour la retenue sur absence, mais la pratique comptable et sociale marocaine utilise généralement la méthode du 30ème (le mois est conventionnellement réputé faire 30 jours, soit `Salaire de base / 30 * Jours d'absence`).
* **Proratisation des plafonds CNSS :** Si un salarié entre dans l'entreprise le 15 du mois, son plafond CNSS (ex: 6 000 DH) doit-il être proratisé à 3 000 DH pour ce mois ? La doctrine de la CNSS impose des règles précises de proratisation au prorata des jours de travail effectifs ou payés déclarés, un point crucial à valider dans vos tests unitaires (Unit Tests).

---

## 7. Recommandations de Validation et Tests d'Audit (QA)
Pour valider votre moteur de calcul avant sa mise en production, vous devez mettre en place une suite de tests automatisés basée sur :
1.  **Les Cas Témoins de la DGI :** Reprenez les exemples chiffrés de la *Note Circulaire 717* de la DGI et vérifiez au centime près que votre code trouve le même montant d'IR.
2.  **Le Test du Calcul à l'envers (Net to Brut) :** L'algorithme doit être capable, à partir d'un Net cible de 10 000 DH, de remonter parfaitement et de manière stable (sans boucle infinie) au Brut Global, en recalculant de manière itérative l'IR et les cotisations.
