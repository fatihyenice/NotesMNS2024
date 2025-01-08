
EXERCICE SQL: 

1) 
SELECT * FROM `villes_france_free` ORDER BY -`ville_population_2012` LIMIT 0,10

2)
SELECT * FROM `villes_france_free` ORDER BY `ville_surface` LIMIT 0,50

3)
SELECT * FROM `villes_france_free` WHERE `ville_departement` LIKE '97%'

4)
SELECT ville_nom,departement_nom FROM `villes_france_free` INNER Join `departement`on`villes_france_free`.`ville_departement` = departement.departement_code order by `ville_population_2012` DESC limit 10

5)
SELECT ville_commune,departement_nom FROM `departement`, `villes_france_free` WHERE departement_code = ville_departement GROUP BY departement_nom ORDER BY -ville_commune

6) SELECT departement_nom,ville_surface FROM departement, villes_france_free WHERE ville_departement = departement_code GROUP BY departement_code ORDER BY -ville_surface LIMIT 0,10;

7)
SELECT COUNT(ville_nom) FROM villes_france_free WHERE ville_nom LIKE 'SAINT%' 

8)
SELECT ville_nom, COUNT(ville_nom) FROM villes_france_free GROUP BY ville_nom ORDER BY -COUNT(ville_nom)

9)

####  SUM(ville_surface) / COUNT(ville_surface) = Calcule de la moyenne de la superficie

SELECT ville_nom FROM villes_france_free WHERE ville_surface > (SELECT SUM(ville_surface) / COUNT(ville_surface) FROM villes_france_free)

10)
SELECT `ville_departement`, SUM(`ville_population_2012`) FROM `villes_france_free` group by `ville_departement` HAVING SUM(ville_population_2012) > 2000000

11)
UPDATE villes_france_free
SET ville_nom = REPLACE(ville_nom, '-', ' ')
WHERE ville_nom LIKE 'SAINT-%'