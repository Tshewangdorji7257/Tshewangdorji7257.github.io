---
Title: DBS101 flipped Class 4
categories: [DBS101, Flipped_Class4]
tages: [DBS101]
---

### Topic : 
----

what i learned:
Objective: To comprehend and apply normal forms in optimizing database designs, emphasizing the significance of reducing databases to normal forms.

Normalization in Database Management Systems
Normalization is essential for:

Eliminating redundant (useless) data ensures data integrity, as repeated data raises the likelihood of inconsistent data.
Normalization helps to keep data consistent by storing it in a single table and referring it everywhere else.
Storage optimization, nevertheless, is not a concern these days because database storage is inexpensive.
Breaking down huge tables into smaller tables with linkages improves the database's scalability and adaptability.
Ensuring data dependencies make sense, i.e. data is stored logically.

Type of normal form:
1.first and second normal form
2.third normal form
3.BCNF
4.fourth normal form


1.First Normal Form (1NF):
The First Normal Form (1NF), which stipulates that a table should possess certain attributes to qualify as normalized. These attributes include:

Single-valued (atomic) attributes/columns.
Uniform domain values within a column.
Unique column names.
Data storage order irrelevance.

Example and Resolution:
A practical example was provided with an Employee table, highlighting a violation of 1NF due to the presence of a multi-valued attribute (emp_skills). To rectify this, two solutions were proposed:

Creating separate tables for Employee and Employee Skills.
Adding multiple rows for multiple skills.

2.Second Normal Form (2NF):
Following the 1NF, attention shifted to the Second Normal Form (2NF), which necessitates adherence to 1NF principles while eliminating partial dependencies within the table structure.

Partial Dependency and Example:
Partial dependency was elucidated as a scenario where columns not included in the primary key depend on only a part of the primary key. An example involving the Students and Subjects tables, along with a Score table, illustrated partial dependency and its resolution.

Resolution and Conclusion:
To normalize the table to 2NF, it was proposed to redistribute the dependent column (teacher_name) from the Score table to the Subjects table, ensuring adherence to 2NF principles and eliminating partial dependency.

3.Third Normal Form (3NF):
Third Normal Form (3NF), which necessitates that a table satisfies both 1NF and 2NF principles while eliminating transitive dependencies. In 3NF, each non-prime attribute is dependent only on the candidate keys and not on other non-prime attributes.

Transitive Dependency:
Transitive dependency was introduced as a scenario where a non-prime attribute depends on another non-prime attribute rather than directly on the primary key. This creates a chain of dependencies, resulting in inefficiency and potential data anomalies.

Example and Analysis:
An example involving the Score table was revisited to illustrate transitive dependency. Additional columns for exam_type and total_marks were introduced, where exam_type was found to depend not only on the primary key (student_id and subject_id) but also on the total_marks column. This transitive dependency violates the principles of 3NF.

Resolution:
To address transitive dependency and normalize the table to 3NF, a separate table for examtype was proposed. This table contains information related to exam types, including total marks and duration. By utilizing the exam_type_id from the ExamType table in the Score table, transitive dependency is eliminated, and the table is normalized to 3NF.

4.BCNF:
BCNF represents a further refinement of database normalization, addressing a specific type of anomaly that may arise in tables normalized to 3NF. To achieve BCNF, certain conditions must be satisfied:

The table must already be in the Third Normal Form (3NF).
Each functional dependency (X → Y) within the table must have X as a super key.

Key Concepts:
Concept of super keys and their significance in determining the applicability of BCNF. Super keys are essential for ensuring that functional dependencies maintain the integrity of the database structure and eliminate redundant data storage.

Example and Analysis:
An illustrative example was provided to demonstrate the conditions required for BCNF. Through a step-by-step analysis of the example table, learned how to identify super keys and evaluate functional dependencies to determine compliance with BCNF criteria.

Achieving BCNF:
Including decomposition of tables and restructuring functional dependencies to ensure dependency preservation. learned how to identify and resolve anomalies such as update, insertion, and deletion anomalies through BCNF normalization.

5.Fourth Normal Form (4NF):
The Fourth Normal Form (4NF), which requires a table to be in BCNF and eliminates multi-valued dependencies. 4NF ensures that there are no non-trivial multi-valued dependencies between attributes.

Multi-Valued Dependency:
Multi-valued dependency was introduced as a scenario where the presence of one or more non-prime attributes can cause a dependency between other non-prime attributes. This can lead to redundancy and potential data anomalies within the database.

Example and Analysis:
An example involving a hypothetical table was presented to illustrate multi-valued dependency. In this example, a table containing information about employees and their projects was examined. It was observed that certain attributes, such as employee skills and project locations, exhibited multi-valued dependencies, violating the principles of 4NF.

Resolution:
To address multi-valued dependency and normalize the table to 4NF, several approaches:

Decomposing the table into multiple tables, each representing a single-valued attribute.
Utilizing foreign keys to establish relationships between related attributes in separate tables.
Ensuring that each attribute in the table is dependent only on the primary key and not on other non-prime attributes.

what i did:
During this session, our class was divided into four groups, each tasked with exploring a specific topic related to database normalization. My group focused on the Third Normal Form (3NF). We engaged in extensive discussions to dissect the significance of 3NF in database design and its practical applications. Our conversation delved into the intricacies of eliminating transitive dependencies and ensuring data integrity through normalization. After thorough deliberation, we presented our insights and findings to the rest of the class, highlighting the key concepts and benefits of adhering to 3NF principles.

conclusion
Finally, lesson on database normalization was both educational and informative. Overall, it was a significant step toward increasing our knowledge and skills in database normalization procedures, providing with useful tools for effective database management in real-world circumstances.





