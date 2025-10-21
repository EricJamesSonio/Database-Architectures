Practicing and learning the database architectures!
 
START DATE : October 21, 2025

[Master - Slave] / [Primary - Replica]
- Having Master (Main) database and Slaves (Clone) of that main database
- For scalability and maintainability!
- Ability to have copies of that main so that if it breaks, theres a back up!
- Slaves can be promoted as Master, when the master falls down!

< ----------------------- RELICATION -------------------------->

[Asynchronous] :
--> Master completed sends the bin log to the slaves and doesn't wait! , the master go

PROS:
--> Faster 

CONS:
--> It's not safe since we don't guarantee if the slaves completed or successful!

[Synchronous] :
--> Master completed sends the bin log to the slaves and wait till all replica's are completed, the master go

PROS:
--> Slower compare to Asynchronous but safer! guarantees that the slaves are completed!

[Semi Asynchronous] :
--> Master completed sends the bin log to the slaves and if theres atleast slaves completed, the master go
--> Basically the middle level!

PROS:
--> Bit faster the synchronous

CONS:
--> Bit less safe than synchronous

< ------------------------------------------------------------------------------------------->

[Requirements]
- Knowledge of Linux terminals!
