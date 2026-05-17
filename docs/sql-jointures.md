# SQL - Les jointures
## INNER JOIN
Retourne uniquement les lignes ayant une correspondance dans les deux tables.
```sql
SELECT e.nom, m.intitule, n.note_finale
FROM etudiants e
INNER JOIN notes n ON n.etudiant_id = e.id
INNER JOIN modules m ON m.id = n.module_id;
```
## LEFT JOIN
Retourne TOUTES les lignes de la table de gauche, meme sans correspondance.
```sql
SELECT e.nom, a.sujet_id
FROM etudiants e
LEFT JOIN affectations_pfe a ON a.etudiant_id = e.id;
-- Les etudiants sans PFE auront sujet_id = NULL
```
## RIGHT JOIN
L'inverse du LEFT JOIN.
## FULL OUTER JOIN
Retourne toutes les lignes des deux tables, avec NULL si pas de correspondance.
## Cas d'usage Smart UPF
Lister les etudiants M1 sans PFE affecte :
```sql
SELECT e.cne, e.nom, e.prenom
FROM etudiants e
LEFT JOIN affectations_pfe a ON a.etudiant_id = e.id
WHERE e.niveau = 'M1' AND a.id IS NULL;
```