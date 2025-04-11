Utilizzando lo stesso database di ieri, eseguite le query in allegato. Caricate un secondo file nella stessa repo di ieri (db-university) con le query di oggi.


📌  JOIN
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
- students
- degrees

```
SELECT `students`.`name` as `student_name`, `students`.`surname`, `students`.`date_of_birth`, `students`.`registration_number`, `degrees`.`name`  as `degree_name`, `degrees`.`level`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'

```


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
- degrees
- departments

```
SELECT `degrees``.name` as `degree_name`, `degrees`.level, `degrees`.`address` as `degree_address`, `departments``.name` as department_name, `departments`.`address` as `deparment_address`
FROM `degrees`
JOIN `departments` ON `departments`.`id`	= `degrees`.`department_id`
WHERE `degrees`.level = 'magistrale'
AND `departments`.`name` = 'Dipartimento di Neuroscienze'

```


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
- courses
- teachers
- course-teacher

```
SELECT `courses`.`name` as `course_name`, `courses`.`period`, `courses`.`cfu`, `teachers`.`name` as `teacher_name`, `teachers`.`surname`, `teachers`.`email`
FROM `courses`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `teachers`.`id` = 44

```


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
- students
- degrees
- departments

```
SELECT `students`.`id` as `student_id`, `students`.`surname` , `students`.`name` as `student_name`, `students`.`registration_number`,
`degrees`.`id` as `degree_id`, `degrees`.`name` as `degree_name`, `degrees`.`level`,  `departments`.`name` as `department_name`, `departments`.`address`
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname` ASC ,  `students`.`name` ASC


```


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
- degrees
- courses
- course_teacher
- teachers

```
SELECT `degrees`.`id` , `degrees`.`name` as `degree_name`, `courses`.`name` as `course_name`, `teachers`.`name` as `teacher_name`,  `teachers`.`surname` as `teacher_surname`
FROM `degrees`
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`

```


6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```
 SELECT DISTINCT teachers.name as teacher_name, teachers.surname, departments.name as department_name
 FROM teachers
 JOIN course_teacher ON course_teacher.teacher_id = teachers.id
 JOIN courses ON courses.id = course_teacher.course_id
 JOIN degrees ON degrees.id = courses.degree_id
 JOIN departments ON departments.id = degrees.department_id
 WHERE departments.name = 'Dipartimento di Matematica'


```


7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.


```


```




📌 GROUP BY
1. Contare quanti iscritti ci sono stati ogni anno
- students

```
 SELECT COUNT(*) as total_student, YEAR(enrolment_date) as year
 FROM students
 GROUP BY YEAR(enrolment_date)

```


2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
-teachers

```
 SELECT COUNT(*) as total_teachers , teachers.office_address  as office_address
 FROM teachers
 GROUP BY teachers.office_address

```


3. Calcolare la media dei voti di ogni appello d'esame

```


```


4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```


```




 RIPASSINO SELECT (extra bonus opzionale per il weekend):
1. Selezionare tutti gli insegnanti
2. Selezionare tutti i referenti per ogni dipartimento
3. Selezionare tutti gli studenti il cui nome inizia per "E" (373)
4. Selezionare tutti gli studenti che si sono iscritti nel 2021 (734)
5. Selezionare tutti i corsi che non hanno un sito web (676)
6. Selezionare tutti gli insegnanti che hanno un numero di telefono (50)
7. Selezionare tutti gli appelli d'esame dei mesi di giugno e luglio 2020 (2634)
8. Qual è il numero totale degli studenti iscritti? (5000)