QUERY GROUP BY:
1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

1. SELECT YEAR(`enrolment_date`) AS `enrolment_year`, COUNT(`id`) AS `subscribers_number` 
FROM `students`
GROUP BY `enrolment_year`;

2. SELECT `office_address`, COUNT(`id`) 
FROM `teachers` 
GROUP BY `office_address`;

3. SELECT `exam_id`, TRUNCATE(AVG(`vote`), 2) AS `vote_average` 
FROM `exam_student` 
GROUP BY `exam_id`;

4. SELECT `department_id`, COUNT(`id`) AS `degrees_number`
FROM `degrees`
GROUP BY `department_id`;

QUERY JOINS:
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami

1. SELECT `students`.`surname`, `students`.`name`, `degrees`.`name` AS `degree_name` 
FROM `students` 
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` 
WHERE `degrees`.`name` = 'Corso di Laurea in Economia' 
ORDER BY `students`.`surname`;

2. SELECT `degrees`.`name` AS `degree_name`, `degrees`.`level`, `departments`.`name` AS `department_name`
FROM `degrees`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' 
AND `degrees`.`level` = 'magistrale';

3. SELECT `courses`.`name` AS `course_name`, `teachers`.`id` AS `teacher_id`, `teachers`.`name`, `teachers`.`surname` 
FROM `course_teacher` 
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` 
JOIN `courses` on `course_teacher`.`course_id` = `courses`.`id` 
WHERE `teachers`.`name` = 'Fulvio'
AND `teachers`.`name` = 'Amato';

4. SELECT `students`.`surname`, `students`.`name`, `degrees`.`name` AS `degree_name`, `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname`, `students`.`name`;

5. SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, `teachers`.`name`, `teachers`.`surname`
FROM `degrees`
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
ORDER BY `degrees`.`name`;