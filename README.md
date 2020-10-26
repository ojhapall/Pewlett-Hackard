# Pewlett-Hackard

Overview of the analysis: Explain the purpose of this analysis.

The purpose of this analysis was to determine the number of retiring employes based on their title. The second purpose of this analysis was to determine who was eligible to participate in a mentorship program.

Results: Provide a bulleted list with four major points from the two analysis deliverables. Use images as support where needed.
* Based on the analysis we are able to conclude that the following number of employees are retiring based on their roles. 
* We can also conclude that 1,941 individual employees are eligible to participate in the mentorship program.
* There are a total of 90,398 employees who will be retiring in the near future. 
* The majority of these retiring employees are either Senior Engineers or Senior Staff.

<img width="163" alt="Retiring Titles" src="https://user-images.githubusercontent.com/68453460/97129727-04ab8100-1716-11eb-8524-70a69ff0501c.png">

Summary: Provide high-level responses to the following questions, then provide two additional queries or tables that may provide more insight into the upcoming "silver tsunami."

How many roles will need to be filled as the "silver tsunami" begins to make an impact?
A total of 90,398 roles will need to be filled. 

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
There are not enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees. Based on the image below we can conclude that there would be roughly 50 staff to each mentor. 

<img width="164" alt="retiring64_titles" src="https://user-images.githubusercontent.com/68453460/97129726-037a5400-1716-11eb-8485-74d30b3f4135.png">
<img width="163" alt="Retiring Titles" src="https://u

Using similar ideology, if we ran the analysis for people born in 1964-01-01 to 1964-12-31 then the data would show that approximately 300,024 people would be eligible for retirement. This shows that 1965 would have a significantly lower number of retiring individuals or potentially more than 90,398 roles to fill if those born in 1964 will be retiring in the same year. 

![Mentoring_title](https://user-images.githubusercontent.com/68453460/97129925-708de980-1716-11eb-90a6-b4745c477545.png)

ADDITIONAL QUERIES

SELECT DISTINCT ON (e.emp_no) e.emp_no, 
e.first_name, 
e.last_name, 
e.birth_date,
de.from_date,
de.to_date,
ti.title
INTO non_retiring_employees
FROM employees AS e
INNER JOIN dept_emp as de
ON (e.emp_no = de.emp_no)
INNER JOIN title as ti
ON (e.emp_no = ti.emp_no)
--WHERE (e.birth_date BETWEEN '1964-01-01' AND '1964-12-31')
ORDER BY e.emp_no ASC;

SELECT COUNT (nre.emp_no), nre.title
INTO retiring64_titles
FROM non_retiring_employees AS nre
GROUP BY nre.title
