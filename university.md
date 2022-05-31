# University_DB

## departments
id: PK
name:
## degree_courses
id: PK
name:
duration: TINYINT
total_university_credits: VARCHAR(3)

## courses
id: PK
name:
year: YEAR
language:
university_credits: TINYINT
total_hours: TINYINT

## teachers
id: PK
firstname:
lastname:
phone_number:
email:

## students
id: PK
firstname:
lastname:
year:
phone_number:
email:

## exam_sessions
id: PK
typology:
duration:

## exam_grades
id: PK
grade: TINYINT
