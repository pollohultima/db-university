Query con Group by

Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(id) AS students_number, year(`enrolment_date`) 
FROM `students` 
GROUP BY YEAR(`enrolment_date`);


Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(id) AS teachers_number, `office_address` 
FROM `teachers` 
GROUP BY `office_address`;


Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`vote`) AS average_vote, `exam_id` 
FROM `exam_student` 
GROUP BY `exam_id`;


Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(id) AS courses_number, `degree_id` AS department 
FROM `courses` 
GROUP BY `degree_id`


Query con Join

Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT * 
FROM `students` 
JOIN `departments` ON `departments`.`id` = `students`.`degree_id` 
WHERE `departments`.`id` = 9;


Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze

SELECT `courses`.*, `departments`.`name` 
FROM `courses` 
JOIN `departments` 
ON `departments`.`id` = `courses`.`degree_id` 
WHERE `departments`.`id` = 7;


Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.*, `teachers`.`name` AS teacher_name, `teachers`.`surname` AS teacher_surname
FROM `course_teacher`
JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `teachers`.`id` = 44;


Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`name`, `students`.`surname`, `departments`.`name` AS department_name, `degrees`.`name` AS degree_name
FROM `degrees`
JOIN `departments`
ON `departments`.`id` = `degrees`.department_id
JOIN `students`
ON `students`.degree_id = `degrees`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC;


Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS degree_name, `courses`.`name` AS course_name, `teachers`.`name` AS teachers_name, `teachers`.`surname` AS teachers_surname
FROM `courses`
JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
ORDER BY `degrees`.`name` ASC;


Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`, `departments`.`name` AS department_name
FROM `course_teacher`
JOIN `courses` 
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `departments`.`id` = 5  
ORDER BY `teachers`.`surname` ASC;

BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami