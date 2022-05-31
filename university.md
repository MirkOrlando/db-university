# University_DB

## departments
id: PK
name: VARCHAR(30) NOTNULL
## degree_courses
id: PK
name:
duration: TINYINT
total_university_credits: VARCHAR(3)

## courses
id: PK
name:
year: TINYINT
language:
university_credits: TINYINT
total_hours: TINYINT

## teachers
id: PK
firstname:
lastname:
phone_number:
email:
address:

## students
id: PK
firstname:
lastname:
year:
phone_number:
email:
address:

## sessions
id: PK
typology:
duration:

## session_student
student_id: PK
student_id: PK
grade: TINYINT
