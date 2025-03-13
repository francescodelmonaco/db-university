1. **Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia**  
SELECT *  
FROM `students`  
JOIN `degrees` ON students.degree_id = degrees.id  
WHERE degrees.name = "Corso di Laurea in Economia";  
---
2. **Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze**  
SELECT *  
FROM `degrees`  
JOIN `departments` ON degrees.department_id = departments.id  
WHERE degrees.level = "magistrale" AND departments.name = "Dipartimento di Neuroscienze"  
---
3. **Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)**  
SELECT course_teacher.teacher_id, course_teacher.course_id, teachers.name, teachers.surname, courses.name, courses. description  
FROM `course_teacher`  
JOIN `teachers` ON course_teacher.teacher_id = teachers.id  
JOIN `courses` ON course_teacher.course_id = courses.id  
WHERE teachers.id = 44;  
---
4. **Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome**  
SELECT students.id, students.name, students.surname, students.degree_id, degrees.name, degrees.department_id, departments.name  
FROM `students`  
JOIN `degrees` ON students.degree_id = degrees.id  
JOIN `departments` ON degrees.department_id = departments.id  
ORDER BY students.surname, students.name ASC;  
---
5. **Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti**  
SELECT courses.degree_id, degrees.name, course_teacher.course_id, courses.name, course_teacher.teacher_id, teachers.name, teachers.surname  
FROM `degrees`  
JOIN `courses` ON degrees.id = courses.degree_id  
JOIN `course_teacher` ON courses.id = course_teacher.course_id  
JOIN `teachers` ON course_teacher.teacher_id = teachers.id  
ORDER BY courses.degree_id ASC;  
---
6. **Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)**  
SELECT DISTINCT course_teacher.teacher_id, teachers.name, teachers.surname, departments.name  
FROM `teachers`  
JOIN `course_teacher` ON teachers.id = course_teacher.teacher_id  
JOIN `courses` ON course_teacher.course_id = courses.id  
JOIN `degrees` ON courses.degree_id = degrees.id  
JOIN `departments` ON degrees.department_id = departments.id  
WHERE departments.name = "Dipartimento di Matematica"  
ORDER BY course_teacher.teacher_id ASC;  
---
7. **BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18**  
SELECT students.*, courses.name, COUNT(exam_student.vote) AS `attempts_number`, MAX(exam_student.vote) AS `max_vote`  
FROM `students`  
JOIN `exam_student` ON students.id = exam_student.student_id  
JOIN `exams` ON exam_student.exam_id = exams.id  
JOIN `courses` ON exams.course_id = courses.id  
GROUP BY students.id, courses.id  
HAVING `max_vote` >= 18  
ORDER BY `attempts_number` DESC;  