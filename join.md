# QUERIES 15/05/2023

## QUERIES JOIN

### QUERY 1
Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`name`, `students`.`surname`, `students`.`registration_number`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

---
### QUERY 2
Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.`name` AS `degree_name`, `degrees`.`level`, `degrees`.`address`, `departments`.`name` AS `department_name`
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

---
### QUERY 3
Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.`name`, `courses`.`description`, `courses`.`period`, `courses`.`year`, `courses`.`cfu`
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`name` = 'Fulvio' AND `teachers`.`surname` = 'Amato' AND `teachers`.`id` = 44;

---
### QUERY 4
Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`surname` AS `student_surname`, `students`.`name` AS `student_name`, `students`.`registration_number`, `degrees`.`name` AS `degree_name`, `degrees`.`level` AS `degree_level`, `degrees`.`address` AS `degree_address`, `departments`.`name` AS `department_name`, `departments`.`address` AS `department_address`, `departments`.`head_of_department`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`;

---
### QUERY 5
Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, `teachers`.`surname` AS `teacher_surname`, `teachers`.`name` AS `teacher_name`
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
ORDER BY `degree_name`, `course_name`, `teacher_surname`, `teacher_name`;

---
### QUERY 6
Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`.*
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';

---
### QUERY 7
BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami

