# ER Diagram Submission - ASWIKA B(212224220013)

## Scenario Chosen:
University

## ER Diagram:

![image](https://github.com/user-attachments/assets/469fcbf7-49c2-434c-9374-52161dc36bd5)



## Entities and Attributes:

STUDENT: REG_NO, STUDENT_NAME,EMAIL,PHONE_NO,D.O.B.
COURSE: COURSE_NAME, COURSE_ID, PREREQUISITE,NO_OF_CREDITS.
INSTRUCTOR:NAME,STAFF_ID,CONTACT,EMAIL,PHONE_NO.

## Relationships and Constraints:


ENROLLMENT: STUDENT enrolls in COURSE (Cardinality and Participation are not explicitly shown, but it implies a many-to-many relationship where a student can enroll in multiple courses and each course can have multiple students. Participation is likely total for ENROLLMENT and partial for both STUDENT and COURSE).

TEACHES: INSTRUCTOR teaches COURSE (This implies a one-to-many relationship where one instructor can teach multiple courses, but each course is taught by one instructor. Participation is likely total for COURSE and partial for INSTRUCTOR).

PREREQUISITE: COURSE has PREREQUISITE (This is a reflexive relationship on the COURSE entity, indicating that a course can be a prerequisite for another course. It is likely an optional many-to-one or many-to-many relationship, where a course can have zero or more prerequisites and can itself be a prerequisite for multiple other courses).```

## Extension (Prerequisite / Billing):

Prerequisite: Prerequisites are modeled through a reflexive relationship on the COURSE entity. The attribute
PREREQUISIT (which should likely be PREREQ_ID to reference another course's ID) in the COURSE entity indicates which course(s)
are required before taking a particular course. This structure allows for defining chains or multiple prerequisites for a single course.

Billing: Billing information is partially modeled through the FEE attribute in the STUDENT entity. This suggests that each student
has an associated fee. However, the diagram doesn't provide details on when or how these fees are applied (e.g., per program, per
semester, per course) or any information about payment status, due dates, or billing history. To model billing more comprehensively,
 you might need additional entities like BILL, PAYMENT, or a more detailed structure within the REGISTRATION or a new enrollment-specific entity to track financial aspects.


## Design Choices:

This ER diagram provides a good foundation for a student registration system, capturing key entities and their relationships.
However, depending on the specific requirements, further refinement might be needed, especially in areas like billing and a clearer
definition of the 'TYPE' attribute in the REGISTRATION entity.

