1. **Contare quanti iscritti ci sono stati ogni anno**  
SELECT YEAR(`enrolment_date`) AS `enrolment_year`, COUNT(`id`) AS `number_of_enrolments`  
FROM `students`  
GROUP BY `enrolment_year`  
ORDER BY `enrolment_year` ASC;  
---
2. **Contare gli insegnanti che hanno l'ufficio nello stesso edificio**  
SELECT `office_address`, COUNT(`id`) AS `number_of_teachers`  
FROM `teachers`  
GROUP BY `office_address`  
ORDER BY `number_of_teachers` ASC;  
---
3. **Calcolare la media dei voti di ogni appello d'esame**  
SELECT `exam_id`, AVG(`vote`) AS `average_votes`  
FROM `exam_student`  
GROUP BY `exam_id`;  
---
4. **Contare quanti corsi di laurea ci sono per ogni dipartimento**  
SELECT `department_id`, departments.name, COUNT(degrees.id) AS `courses_by_department`  
FROM `degrees`  
JOIN `departments` ON degrees.department_id = departments.id  
GROUP BY `department_id`;  