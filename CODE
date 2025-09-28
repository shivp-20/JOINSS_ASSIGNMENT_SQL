USE HR;
-- 1. Write a query to find the addresses (location_id, street_address, city, state_province, country_name) of all the departments. 
select l.location_id,l.street_address,l.city,l.state_province,c.country_name,d.*
from departments d
join locations l on l.location_id = d.location_id
join countries c on c.country_id = l.country_id;




-- 2. Write a query to find the name (first_name, last name), department ID and name of all the employees 
select first_name,last_name,department_id,e.*
from employees e;




select * from countries;
select * from regions;
-- 3. Write a query to find the name (first_name, last_name), job, department ID and name of the employees who works in London. 
select e.first_name,e.last_name,j.job_title,e.department_id,concat(e.first_name,"-",e.last_name) as full_name
from employees e
join jobs j on j.job_id = e.job_id
join departments d on d.department_id = e.department_id
join locations l on l.location_id = d.location_id 
join countries c on c.country_id = l.country_id
where c.country_name = 'london';



-- 4. Write a query to find the employee id, name (last_name) along with their manager_id and name (last_name). 
select e.employee_id, e.last_name ,d.department_name, concat(e.manager_id,'-',e.last_name)
from employees e
join departments d on d.department_id = e.department_id;



-- 5. Write a query to find the name (first_name, last_name) and hire date of the employees who was hired after 'Jones'. 
select * from employees
where last_name = 'jones';
select e.first_name,e.last_name,e.hire_date
from employees e
where e.hire_date > (
    SELECT hire_date
    FROM employees
    WHERE last_name = 'Jones'
);

-- 6. Write a query to get the department name and number of employees in the department. 
select d.department_name,count(employee_id) as no_emp
from employees e
join departments d on d.department_id = e.department_id
group by d.department_name;



-- 7. Write a query to find the employee ID, job title, number of days between ending date and starting date for all jobs in department 90. 
select e.employee_id,j.job_title,count(timestampdiff(day, jh.end_date,jh.start_date)) as days
from employees e
join jobs j on j.job_id = e.job_id
join job_history jh on jh.job_id =  j.job_id
where e.department_id =90
group by 1,2;



-- 8. Write a query to display the department ID and name and first name of manager. 
select e.department_id, d.department_name, concat(e.manager_id,'-',e.first_name)
from employees e 
join departments d on d.department_id = e.department_id;



-- 9. Write a query to display the department name, manager name, and city.
select d.department_name , e.manager_id,e.first_name,l.city
from employees e 
join departments d on d.department_id = e.department_id
join locations l on l.location_id = d.location_id;


-- 10. Write a query to display the job title and average salary of employees. 
select j.job_title, avg(salary) as avg_salary
from employees e 
join jobs j on j.job_id = e.job_id
group by j.job_title;




-- 11. Write a query to display job title, employee name, and the difference between salary of the employee and minimum salary for the job. 
select j.job_title, e.first_name, e.last_name ,(e.salary - j.min_salary)
from employees e
join jobs j on j.job_id = e.job_id;


-- 12. Write a query to display the job history that were done by any employee who is currently drawing more than 10000 of salary. 
select jh.*, e.salary
from job_history jh
join employees e on e.job_id = jh.job_id
where e.salary > 10000;


-- 13. Write a query to display department name, name (first_name, last_name), hire date, salary of the manager for all managers whose experience is more than 15 years.
select d.department_name, e.first_name, e.last_name, e.hire_date , e.manager_id
from employees e
join departments d on d.department_id = e.department_id 
WHERE e.hire_date <= ADDDATE(CURDATE(), INTERVAL -15 YEAR);



