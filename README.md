# texts
use [AdventureWorks2012] EXEC sp_changedbowner 'sa'

/* 1.	Count how many different JobTitles exist among employees. (Consider using: HumanResources.Employee) */
--select [JobTitle] from [HumanResources].[Employee] order by JobTitle
--select JobTitle from [HumanResources].[Employee] group by JobTitle
--select LoginID, count(*) as "Rows count", count(JobTitle) as "Not null job titles count", count(distinct JobTitle) as "Unique job titles count" from [HumanResources].[Employee]
--group by LoginID

--2.	Retrieve all information from Product table regarding all products not containing Metal in their names. (Consider using: Production.Product)
--select * from [Production].[Product] where name like '_h%'

--3.	Show JobTitle, HireDate, FirstName, LastName of those employees who were hired 
--before first of January 2002. Order records by HireDate. (Consider using: HumanResources.Employee, person.Person)

go
create view vEmployees as
select e.JobTitle as 'Emp job title', e.HireDate as 'Emp hire date', p.FirstName as 'Pers first name', p.LastName as 'Pers last name'
from HumanResources.Employee e 
	join Person.Person p on e.BusinessEntityID = p.BusinessEntityID
where e.HireDate < '2008-01-01'

select * from vEmployees order by [Emp hire date] desc

--4.	Display all product names and corresponding culture names. (Consider using: Production.Product, production.ProductModelProductDescriptionCulture, Production.Culture)
--select *
--from Production.Product p
--	join Production.ProductModelProductDescriptionCulture and pr 
