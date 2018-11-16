# ER Model
## Basics
- Conceptual design questions to consider:
  - What are the objects you're dealing with? The relationships?
  - What do you need to know about them? What should be stored in the database?
  - What other things must be considered?
- ER Model (entity-relationship model): allows us to describe the data involved in real-world enterprise in terms of objects and their 
    relationships 
  - **Entity**: object in the real world that you want to represent in the database, distinguishable from other objects
      Ex. Students and teachers
      ```
      (_ssn_)  (name)   (parking_lot) <- attributes, an underlined attribute is a key 
          \      |       /
           [  employee  ] <- entity 
    ```
  - **Entity set**: collection of similar entities, all entities in this set have the same attributes and a key that identifies them
    - The key can be 1+ attributes
    - Each attribute has a domain of possible values
      Ex. name:string, sid:integer
  - **Relationship**: association among 2+ entities, can also have attributes (called descriptive attributes)
  - **Relationship set**: collection of similar relationships
    - One entity set can participate in different relationship sets, different "roles" in the same set
  - Cardinality constraints: 1:1, 1:N (one-to-many), N:1 (many-to-one), M:N (many-to-many)
      Ex. A department can have only 1 manager but multiple employees (1:N)
  - Participation constraints: heavy lines indicate required participation (thick or double line)
    - Partial (single line) vs. total (double/thick line) participation 
      Ex. Can't be a department without a manager
      ```         
      [employee] ----- < manages > ====== [departments] //not every employee has to be a manager, but departments must be managed
      [        ] ===== < works_in > ===== [           ] //every employee must work in a department
      ```
  - Complicated constraints are difficult to model, ex. the professor has to be in the department s/he's a head of 

## Advanced Concepts
- **Weak entity**: identified uniquely only by considering the primary key of another (owner/strong) entity
  - Owner entity set and weak entity set must participate in a 1-to-many relationship (1 owner to many weak entities)
  - Must have total participation in this identifying relationship set
  - Not in database unless it has a parent
  - Their keys are identified by a dotted line, needs to be paired w/ strong entity primary key to be uniquely identified
  - Once an employee is removed from DB, so are all his/her dependents
   ```   
      (_ssn_)                             (_ _pname_ _) //dotted line = key for a weak entity, can have multiple of the same 
         |        1                 M           |
    [employee] ----- << policy >> ===== [[dependent]] //weak entity
     //owner ent                //thick line here = total participation required by weak entity in this relationship 
    ```
- **Ternary relationships**: relationship key <= entity keys, relationship between >2 entities
      Ex. A prescription is a 3-way relationship between patient, doctor, and drug
- ISA hierarchy:
  - **ISA relationship**: if declare "ISA", every A entity is considered a B entity if A ISA B
  - Covering constraints: 
        Ex. Students and Instructors COVER User, means that these are the only two types of users in the model/system
  - Overlap constraints: 
        Ex. Students OVERLAPS Instructors, means that a student can be an instructor (TA)
   - Much like inheritance, Students and Instructors have all the attributes of User
   - Can add descriptive attributes to a subclass 
        Ex. (major) ----- [student], (title) ----- [instructor]
   - Design: specification (top-down), generalization (bottom-up)
- **Aggregation**: dumping/aggregating things together
    o When you want to model a relationship involving a relationship set
    o Allows you to treat a relationship set as an entity set for purposes of participating in other relationships
    o The relationship set is treated as an entity, is surrounded with a dotted rectangle
    o Not the same as a ternary relationship 
- Other ER features:
    o **Multi-valued attributes**: entity can have 1+ of these, surrounded by a double-lined circle 
        Ex. Phone 
    o **Composite attributes**: an attribute made up of multiple other attributes
        Ex. Name -> first and last name
    o Derived attributes: attributes derived from other attributes, surrounded by a dotted circle 
 - Design choices: should it be an entity, attribute? Nouns tend to be entities, things that are logically separate and referrable 
    should be an entity
 - Binary vs. ternary relationships 
 - Database design process/flow: requirement gathering (interviews/requirements analysis), conceptual design (using ER, goal is to 
    create a single description of the data that closely mathces how users and devs think of the data), platform choice (which DBMS?), 
    logical design (for target data model), physical design (for target DBMS, workload), implement (and test)
- Summary of conceptual design:
  - Follows requirements analysis
  - ER is a popular conceptual design
  - **Basic constructs**: entities, relationships, attributes
  - **Additional constructs**: weak entities, ISA hierarchies, aggregation, multivalued, composite, and/or derived attributes
  - There are many variations of ER model
  - **Several integrity constraints**: cardinality, participation, overlap/covering, foreign key constraints
  - ER design is subjective
  - Ensure good DB design
