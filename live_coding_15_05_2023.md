# LIVE CODING 15/05/2023

## QUERY 1 LIVE CODING
Selezionare le informazioni sul corso con id = 144, con tutti i relativi appelli d’esame

SELECT `courses`.`id` AS `course_id`, `courses`.`name` AS `course_name`, `exams`.`id` AS `exam_id`, `exams`.`date` AS `exam_date`
FROM `courses`
JOIN `exams` ON `courses`.`id` = `exams`.`course_id` 
WHERE `course_id` = 144;

---
## QUERY 2 LIVE CODING
Selezionare a quale dipartimento appartiene il Corso di Laurea in Diritto dell'Economia (Dipartimento di Scienze politiche, giuridiche e studi internazionali)

SELECT `departments`.*
FROM `departments`
JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Diritto dell\'Economia';

---
## QUERY 3 LIVE CODING
Selezionare tutti gli appelli d'esame del Corso di Laurea Magistrale in Fisica del primo anno

SELECT `courses`.`name` AS `course_name`, `courses`.`year`, `courses`.`cfu`, `exams`.`date`, `exams`.`address`, `degrees`.`name` AS `degree_name`
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `exams` ON `courses`.`id` = `exams`.`course_id`
WHERE `degrees`.`name` = 'Corso di Laurea Magistrale in Fisica'
AND `courses`.`year` = 1;

---
## QUERY 4 LIVE CODING
Selezionare tutti i docenti che insegnano nel Corso di Laurea in Lettere (21)

SELECT DISTINCT `teachers`.*
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Lettere';

---
## QUERY 5 LIVE CODING
Selezionare il libretto universitario di Mirco Messina (matricola n. 620320)

SELECT `students`.`name`, `students`.`surname`, `students`.`registration_number`, `courses`.`id`, `courses`.`name`, `exams`.`date`, `exam_student`.`vote`
FROM `exam_student`
JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses`ON `exams`.`course_id` = `courses`.`id`
WHERE `students`.`name` = 'Mirco'
AND `students`.`surname` = 'Messina'
AND `exam_student`.`vote` >= 18;

---
## QUERY 6 LIVE CODING
Selezionare il voto medio di superamento d'esame per ogni corso, con anche i dati del corso di laurea associato, ordinati per media voto decrescente

SELECT AVG(`exam_student`.`vote`) AS `average_vote`, `courses`.`name` AS `course_name`, `degrees`.`name` AS `degree_name`
FROM `exam_student`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
WHERE `exam_student`.`vote` >= 18
GROUP BY `courses`.`id`
ORDER BY `average_vote` DESC;
