# Schéma de la base de données

## Tables principales

| Table            | Champs |
|------------------|--------|
| **Role**         | id, nom |
| **User**         | id, nom, prénom, username, password, role_id |
| **Patient**      | id, nom, prénom, date_naissance, sexe, email, tel, password, role_id |
| **Medecin**      | id, nom, prénom, specialite, username, password, role_id |
| **Analyse**      | id, nom, description, prix |
| **ValeurReference** | id, sexe, age_min, age_max, valeur_min, valeur_max, unite, analyse_id |
| **Examen**       | id, date, patient_id, medecin_id, prix |
| **ExamenElement**| id, analyse_id, laborantin_id, examen_id |
| **Résultat**     | id, valeur, examen_element_id, anomalie, commentaire |
| **Paiement**     | id, date, montant, examen_id, user_id |
| **RendezVous**   | id, date, patient_id, medecin_id, motif, statut |

---

## Contraintes et énumérations

- **anomalie** : boolean  
- **sexe** : enum('Homme', 'Femme')  
- **statut** : enum('En attente', 'Confirmé', 'Annulé', 'Terminé')  

---

## Détails supplémentaires

- **Medecin.specialite** : spécialité du médecin (ex: Cardiologue, Dermatologue, Généraliste, etc.)  
- **Analyse.prix** : prix de l'analyse  
- **ValeurReference.sexe** : sexe applicable  
- **ValeurReference.age_min / age_max** : tranche d’âge applicable  
- **ValeurReference.valeur_min / valeur_max** : bornes minimales et maximales de référence  
- **ValeurReference.unite** : unité de mesure  
- **ExamenElement.laborantin_id** : laborantin qui a réalisé l'examen  
- **Résultat.valeur** : valeur mesurée  
- **Résultat.anomalie** : indique si la valeur est hors normes  
- **Résultat.commentaire** : commentaire additionnel  
- **Paiement.user_id** : user ayant enregistré le paiement  
- **Paiement.date** : date du paiement  
- **Paiement.montant** : montant payé  
- **Paiement.examen_id** : examen concerné  

---

## Exemple

Examen 20/09 pour patient 1, medecin 2 prix total : 34$ (patient homme 30 ans)

FNS 20$ => FNS pour homme 30 ans : 4.5 - 11.0 g/L => 8.0 g/L
HDL 13$ => HDL pour homme 30 ans : 1.0 - 1.5 g/L => 1.9 g/L
LDL 5$  => LDL pour homme 30 ans : 0.5 - 1.6 g/L => 1.0 g/L

Paiement 34$ pour examen 1

Rendez-vous 25/09 pour patient 1, medecin 2
