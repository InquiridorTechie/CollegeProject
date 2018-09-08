## Models

Model_Name            | Description
----------------------|-------------------------------------------------------------------------------------------------
Subject               | Used to store `subject_name` and its corresponding `paper_id`.
Teacher               | Used to store `teacher_name` and their `department`.
TeacherSubjectMapping | Used to hold the relationship between Subject and Teacher model. Eg. X teacher teaches Y subject.
Section               | It holds the `section`, `branch`, `year`, `shift` and Teacher -----> Subject record of a particular class.
Feedback	            | Used to store feedback of every teacher on the basis of the subject he/she teaches.

## Model's Fields

**1. Subject**

Field_Name	    | Field_Type | Description
----------------|------------|--------------------------------------------------------------------
**id**		      | UUIDField  | This is an autogenerated field created by django for the primary key to uniquely identify the record of the table.
**subject_name**| CharField  | This field is used to store all subject names in the database.
**paper_id**	  | CharField  | This field is used to store the paper id of each subject in the database.

**2. Teacher**

Field_Name	    | Field_Type | Description
----------------|------------|---------------------------------------------
**id**		      | UUIDField  | This is an autogenerated field created by django for the primary key to uniquely identify the record of the table.
**teacher_name**| CharField  | It stores every teacher name in the database.
**teacher_dept**| CharField  | It stores department name of each teacher in the database.


**3. TeacherSubjectMapping**

Field_Name	    | Field/Relation  | Description
----------------|-----------------|----------------------------------------------------------------------------------
**id**		      | UUIDField	      | This is an autogenerated field created by django for the primary key to uniquely identify the record of the table.
**teacher_name**| ForeignKey	    | It acts like a foreign key and take input values from the `teacher_name` field of Teacher model.
**subject_name**| ForeignKey	    | It also acts like a foreign key and take input values from the `subject_name` field of Subject model.

**4. Section**

Field_Name      | Field/Relation  | Description
----------------|-----------------|-----------------------------------------------------------------------------
**id**          | UUIDField	      | This is an autogenerated field created by django for the primary key to uniquely identify the record of the table.
**section_name**| CharField	      | It is used to store section name of every branch in the database.
**year**        | IntegerField    | It is used to store the year of the corresponding section.
**branch**      | CharField	      | It defines the branch name of the corresponding section.
**shift**       | IntegerField	  | It defines the shift of the section. It could be either 1st or 2nd shift.
**subjects**    | ManyToManyField | This field maps with the TeacherSubjectMapping model with many-to-many relation.
**feedback**    | ManyToManyField | This field maps with the Feedback model with many-to-many relation.

**5. Feedback**

Field_Name	          | Field/Relation | Description
----------------------|----------------|----------------------------------------
**id**	              | UUIDField      | This is an autogenerated field created by django for the primary key to uniquely identify the record of the table.
**teacher**	          | ForeignKey     | It acts like a foreign key and take input values from the `teacher_name` field of Teacher model.
**section**	          | ForeignKey     | It acts like a foreign key and take input values from the `section_name` field of Section model.
**Punctuality**	      | IntegerField   | It stores min=1 and max=5 rating for punctuality of a teacher.
**Subject_knowledge** | IntegerField   | It stores min=1 and max=5 rating for subject knowledge of a teacher.
**Behaviour**	        | IntegerField   | It stores min=1 and max=5 rating for behaviour of a teacher.
**Method_of_teaching**| IntegerField   | It stores min=1 and max=5 rating for method of teaching of a teacher.
**Audibility**	      | IntegerField   | It stores min=1 and max=5 rating for audibility of a teacher.
**Syllabus_coverage** | IntegerField   | It stores min=1 and max=5 rating for syllabus coverage of a teacher.

### All models have ```__str__``` method, returning a human-readable, descriptive, short text.