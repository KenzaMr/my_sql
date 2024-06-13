# LMD : Langage de Manipulation de Données (DML : Data Manipulation Language)
### Insérer des données (CREATE)
 ```sql
 INSERT INTO  movie (nom, date_sortie) VALUES ('Pulp Fiction', '2001-10-23'), ('The Revenant','2015-04-30');
 ```
 ### Afficher les données (READ)
 ```sql
 SELECT * FROM director WHERE (conditions);
 SELECT * FROM director WHERE age BETWEEN 40 AND 60;
 SELECT * FROM director WHERE prenom LIKE 'an%';
 SELECT * FROM director WHERE prenom IN ('Nolan','Sam')

 ```
 ### Mettre à jour les données (UPDATE)
 ```sql
UPDATE director SET nom='test', prenom= 'test'
-- Tous les pays seront sur Fr pour les id de 0 à 10
UPDATE director SET pays_dorigine= 'Fr' WHERE id BETWEEN 0 AND 10 ;
-- Modifier le salaire à 1 millions pour les realisateurs qui ont moins de 20ans ou entre 40 et 60 ans
UPDATE director SET salary = '1000000' WHERE age<=20 OR age BETWEEN 40 AND 60;
-- Mettre à jour la colonne salaire pour pouvoir avoir 14 chiffres dont 2 aprés la virgule 
ALTER TABLE director MODIFY salary DECIMAL (14,2);
 ```
### Supprimer des données (DELETE)
```sql
DELETE FROM director 
-- Supprimer les réalisateurs qui n'ont pas la valeur Fr ou An en guise de pays 
DELETE FROM director WHERE pays_dorigine != 'Fr' AND pays_dorigine != 'An';
DELETE FROM director WHERE pays_dorigine  NOT IN ('Fr','An');
```
EXERCICE
 ```sql
  <!-- Inserer 4 realisateur dans director -->
 INSERT INTO director (nom) VALUES ('Nolan'),('Raimi'),('Spielbierg'),('Besson')
 INSERT INTO director(prenom)VALUES('Chistopher'),('Sam'),('Steven'),('Luc')
 INSERT INTO director (nom,prenom,age,email,date_de_naissance,salary,pays_dorigine) VALUES ('Nolan','Christopher','53','christotent@gmail.com','1970-07-30','15931','Angleterre'),('Raimi','Sam','64','raimiSam@hotmail.com','1959-10-23','78945','Etats-Unis'),('Spielbierg','Steven','77','steste@rea.com','1946-12-18','9550','Etats Unis'),('Besson','Luc','65','bessonrea@hotmail.com','1959-03-18','65423','France');
 ```
 EXERCICE
 ```sql
 <!-- Afficher le prenom et l'email des realisateur dont le nom contient un 'e' et ou le pays est FR ou AN et age est suppérieur à 30ans -->
SELECT email,prenom FROM director WHERE nom LIKE '%e%' AND pays_dorigine = 'Fr' OR pays_dorigine ='An' AND age > 30;
SELECT email,prenom FROM director WHERE nom LIKE '%e%'AND pays_dorigine IN ('Fr','Et') AND age > 30 ORDER BY email;
SELECT email, prenom FROM director ORDER BY email LIMIT 1
 ```
 
