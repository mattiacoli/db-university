Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

  sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
  ogni Dipartimento offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
  ogni Corso di Laurea prevede diversi **Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
  ogni Corso può essere tenuto da diversi **Insegnanti**;
  ogni Corso prevede più **appelli d'Esame**;
  ogni **Studente** è iscritto ad un solo Corso di Laurea;
  ogni Studente può iscriversi a più appelli di Esame;
  per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
  Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.


## name Table `departments`  PRIMARY

**Columns:**
- id (INT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- name (VARCHAR(255)) – NOT NULL

---

## name Table `degree_courses`  SECONDARY
**Columns:**
- id (INT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- department_id (INT) – FOREIGN KEY – NOT NULL
- name (VARCHAR(255)) – NOT NULL


---

## name Table `courses`  SECONDARY
**Columns:**
- id (INT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- degree_course_id (INT) – FOREIGN KEY  – NOT NULL
- name (VARCHAR(255)) – NOT NULL

---

## name Table `exam_appeals`  SECONDARY
**Columns:**
- id (BIGINT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- course_id (INT) – FOREIGN KEY REFERENCES  – NOT NULL
- teacher_id (INT) – FOREIGN KEY REFERENCES  – NOT NULL
- date (DATETIME) – NOT NULL



---

## name Table `teachers`  PRIMARY
**Columns:**
- id (INT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- name (VARCHAR(100)) – NOT NULL
- lastname (VARCHAR(100)) – NOT NULL



---

## name Table `students` PRIMARY
**Columns:**
- id (BIGINT) – PRIMARY KEY – AUTO_INCREMENT – NOT NULL
- name (VARCHAR(100)) – NOT NULL
- lastname (VARCHAR(100)) – NOT NULL
- degree_course_id (INT) – FOREIGN KEY – NOT NULL


---



## Table: `course_teacher` (Pivot)

**Columns:**
- course_id (INT) – FOREIGN KEY – NOT NULL
- teacher_id (INT) – FOREIGN KEY – NOT NULL


---

## Table: `exam_appeal_student` (Pivot)

**Columns:**
- exam_appeal_id (INT) – FOREIGN KEY – NOT NULL
- student_id (INT) – FOREIGN KEY – NOT NULL
- vote (TINYINT) – NOT NULL





