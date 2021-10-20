# Pewlett-Hackard-Analysis
 ## Overview ##
   Purpose of analysis is to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. 

## Results ##

* From the finding of the eligible retirees, High Percentage of the workforce could retire at any given time.
*From the job titles of the eligible retirees, the breakdown is below.
*21776,Senior Engineer
*21077,Senior Staff
*10620,Engineer
*9195,Staff
*3392,Technique Leader
*1305,Assistant Engineer
*1,Manager

## Summary ##
The summary addresses the two questions and contains two additional queries or tables that may provide more insight
1) How many roles will need to be filled as the "silver tsunami" begins to make an impact?.
67,366 roles are in urgent need to be filled out as soon as the workforce starts retiring at any given time.

2) Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?

Yes, we have 90,398  employees who are eligible to participate in a mentorship program.

--Write a query to create a Mentorship Eligibility table that holds the employees who are eligible to participate in a mentorship program. 
SELECT DISTINCT ON(e.emp_no)e.emp_no,
	e.first_name,
	e.last_name,
	e.birth_date,
	de.from_date,
	de.to_date,
	t.title
--INTO mentorship_eligibilty
FROM employees as e
Left outer Join dept_emp as de
ON (e.emp_no = de.emp_no)
Left outer Join titles as t
ON (e.emp_no = t.emp_no)
WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31')
ORDER BY e.emp_no;
