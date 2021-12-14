SELECT * 
FROM `students` 
WHERE `date_of_birth` 
BETWEEN '1990-01-01' AND '1990-12-31';


SELECT * 
FROM `courses` 
WHERE `cfu` > '10';


SELECT * 
FROM `students` 
WHERE YEAR(date_of_birth) < '1991';


SELECT * 
FROM `courses` 
WHERE `year` = 1 
AND `period` = 'I semestre';


SELECT * 
FROM `exams` 
WHERE `hour` > '14:00:00' 
AND `date` = '2020-06-20';


SELECT * 
FROM `degrees` 
WHERE `level` = 'magistrale';


SELECT COUNT(id) 
FROM `departments`;


SELECT COUNT(id) 
FROM `teachers` 
WHERE `phone` IS NULL;