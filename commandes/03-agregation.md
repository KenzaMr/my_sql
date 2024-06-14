```sql
<!-- Créer une base de donnée agregation -->
create database agregation ;
<!-- Créer une table ville_notation id,nom,note, code_pays -->
create table ville_noation(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(255),
    note INT,
    code_pays CHAR(2)
);
<!-- Insérer 10 lignes de villes code_pays et la note-->
INSERT INTO ville_noation(nom, note, code_pays)values ('Tremblay',7,'Fr'),('Reims',6,'Fr'),('Cachan',4,'Fr'),('Marseille',5,'Fr'),('Oran',1,'Dz'),('Chelsea',6,'Uk'),('Londres',4,'Uk'),('Alger',7,'Dz'),('Nantes',7,'Fr'),('Lille',8,'Fr');
-- Afficher la note minimal 
SELECT MIN(note) FROM ville_noation;
-- Afficher la note maximal
SELECT MAX(note) FROM ville_noation;
-- Afficher la moyenne 
SELECT AVG(note) FROM ville_noation;
-- Donnez une condition sur l'agregation
SELECT AVG(note), code_pays FROM ville_noation GROUP BY code_pays HAVING AVG(note)>5;
<!-- ORDRE DES CLAUSES -->
SELECT
FROM
JOIN
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
-- Afficher les notes minimum par code pays supérieur à 2 trier par code pays
SELECT MIN(note), code_pays FROM ville_noation GROUP BY code_pays HAVING MIN(note)>2;
-- Faire la moyenne des notes sans compter les 1 par pays en exluant les moyennes inférieur à 2 trier par code pays
SELECT AVG(note), code_pays FROM ville_noation WHERE note != 1 GROUP BY code_pays  HAVING AVG(note)>2 ORDER BY code_pays;

```