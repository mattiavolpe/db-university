# QUERIES 15/05/2023

## QUERIES JOIN

### QUERY 1
Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;

---
### QUERY 2
Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze



---
### QUERY 3
Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)



---
### QUERY 4
Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome



---
### QUERY 5
Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti



---
### QUERY 6
Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)



---
### QUERY 7
BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
