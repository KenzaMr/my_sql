# LDD : Langage de Définition de Données (DDL: Data Definition Language)

### Affichege des tables:
```sql
SHOW TABLES;
```
 ### Création d'une table:
 ```sql 
CREATE TABLE nom_table(
    id INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(255),
    date_sortie DATE DEFAULT '2000-01-01'
);
 ```
### Afficher la structure de la table: 
```sql
DESCRIBE nom_table;
```
### Afficher le create table:
```sql
SHOW CREATE TABLE nom_table;
```
<!-- Créer une table réalisateur -->
<!-- id -->
<!-- nom (pas le droit d'etre null) -->
<!-- prenom (pas me droit d'etre null)-->
<!-- age (verifier qu'il a plus de 18 ans ) -->
<!-- email (mais il doit etre unique) -->
<!-- date de naissance par défaut date du jour -->
<!-- Salaire (qui pourra être un nombre à virgule) -->
### Exercice
```sql
CREATE TABLE realisateur (
    id INT UNSIGNED PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(200)NOT NULL,
    prenom VARCHAR(200)NOT NULL,
    age TINYINT UNSIGNED CHECK (age >=18),
    email VARCHAR(200) UNIQUE,
    date_de_naissance DATE DEFAULT CURDATE(),
    salaire DECIMAL (8,2) UNSIGNED 
);
```
<!-- On s'est tromper -->


### Exercice 2
```sql
<!-- Rennommer la table realisateur en director -->
RENAME TABLE realisateur TO director;
<!-- Rennommer la table films en movie  -->
RENAME TABLE films TO movie;
<!-- Modifier la table director pour ajouter la colonne pays d'origine => 'FR' -->
ALTER TABLE director ADD pays_dorigine CHAR(2);
<!-- Modifier la colonne salaire pour que le type soit decimal (10,2) -->
ALTER TABLE director MODIFY salaire DECIMAL(10,2);
<!-- Modifier le nom salaire en salary  -->
ALTER TABLE director CHANGE salaire salary DECIMAL(10,2);
<!-- Modifier la table movie pour rajouter la contrainte unique sur le nom du film -->
ALTER TABLE movie ADD CONSTRAINT UNIQUE (nom);
<!-- Retirer la contrainte unique -->
ALTER TABLE movie DROP INDEX nom;
<!-- Créer une table test avec un id  -->
CREATE TABLE test(
    id INT PRIMARY KEY
);
<!-- Supprimer la table test -->
DROP TABLE test;
```

```sql
<!-- Ajouter une colonne id_director dan la table movie avec le bon type  -->
ALTER TABLE movie ADD COLUMN id_director INT ;
<!-- Ajouter une clé secondaire dans la table movie  -->
ALTER TABLE movie ADD CONSTRAINT fk_id_director FOREIGN KEY (id_director) REFERENCES director (id);
```