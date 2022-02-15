# SQL_ifnull_coalesce_
Hi everyone, this is my initial step on SQL. Here I did some small queries using ifnull and coalesce function. 

/* In order to show example of IFNULL or COALESCE, we would need NULL values in our dataset.
So, I have decieded to change dep_duplicate table. */


- Alter table dep_duplicate
change column dept_name dept_name VARCHAR(40) NULL;
select * from dep_duplicate; -

/* here I changed column dept_name, so it can have NULL values */

- insert into dep_duplicate(dep_no)
values ('d008'), ('d009');
select * from dep_duplicate; -

/* In order to have null values, I added to rows to our table, missing dep_names */ 

- alter table dep_duplicate
add column dep_manager VARCHAR(40) NULL after dept_name;
select * from dep_duplicate; -

/* Adding new column would be needed for COALESCE example */
		
		--- /* LET'S USE IFNULL */ ---
        
- select dep_no, dept_name, ifnull(dept_name, 'NO DATA') as IFNULL_
from dep_duplicate;  -

/* so now, you can differentiate dept_name column with new_table column, where ifnull function applied. */

		--- /* LET"S USE COALESCE */ ---

- select dep_no, dept_name, coalesce(dep_manager, dept_name, 'NO DATA') as COALESCE_
from dep_duplicate; -
