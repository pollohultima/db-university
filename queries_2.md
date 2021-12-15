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
Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami