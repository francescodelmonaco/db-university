1. **Selezionare tutti gli studenti nati nel 1990 (160)**  
SELECT *  
FROM `students`  
WHERE YEAR(`date_of_birth`) = 1990  
ORDER BY `id` ASC;  
---
2. **Selezionare tutti i corsi che valgono più di 10 crediti (479)**  
SELECT *  
FROM `courses`  
WHERE `cfu` > 10  
ORDER BY `id` ASC;  
---
3. **Selezionare tutti gli studenti che hanno più di 30 anni**  
SELECT *  
FROM `students`  
WHERE 2025 - YEAR(`date_of_birth`) >= 30  
ORDER BY `date_of_birth` DESC;  
---
4. **Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)**  
SELECT *  
FROM `courses`  
WHERE `period` = "I semestre" AND `year` = 1  
ORDER BY `id` ASC;  
---
5. **Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)**  
SELECT *  
FROM `exams`  
WHERE HOUR(`hour`) >= 14 AND `date` = "2020/06/20"  
ORDER BY `hour` ASC;  
---
6. **Selezionare tutti i corsi di laurea magistrale (38)**  
SELECT *  
FROM `degrees`  
WHERE `level` = "magistrale"  
ORDER BY `id` ASC;  
---
7. **Da quanti dipartimenti è composta l'università? (12)**  
SELECT COUNT(*) AS `number_of_departments`  
FROM `departments`;  
---
8. **Quanti sono gli insegnanti che non hanno un numero di telefono? (50)**  
SELECT COUNT(*) AS `teachers_without_phone`  
FROM `teachers`  
WHERE `phone` IS NULL;  