Blood donation system question

1.Find night shifts for receptionist and their name starts with 'a' (where / AND / like)

	SELECT * from receptionist where receptionist_shift = 'night' and 
	receptionist_name LIKE "a%";

2.Find patients with blood type A or AB (where / in ) 

	SELECT * from patient where patient_bloodType in ('A','AB');
 
3.Find patients names who have 40 years old or less and female (where / AND)
	
	SELECT patient_name , patient_age , patient_gender from patient 
	where patient_age => 40 AND patient_gender = 'female';
	

4.Sort birth dates of patients from eldest to youngest (orderBY DESC)

	SELECT patient_name , patient_age from patient order by patient_age desc;

5.Find the total amount in the stock (SUM / As / group by /order by)

	SELECT stock_id , SUM(stock_amount) as totalAmount from stock GROUP BY 
	stock_id ORDER BY stock_id ;


6.find the avarage age of female patients (where / AVG / AS)
	
	SELECT AVG(patient_age) AS avgFemale from patient 
	where patient_gender = 'female';
	
	
7.increase the total number of requests by 5 (count )

	SELECT count(*) + 5 as newReqNum from request ;

8.count all the patients that older than the avarage age (count / having / groub by)
	SELECT patient_name , count(*) from patient HAVING AVG(patient_age) < 		patient_age GROUB BY patient_name;

9.List all the nurses and patients names (inner join)

	SELECT patient.patient_name , nurse.nurse_name INNER JOIN patient on 
	nurse.nurse_id = patient.nurse_id;

10.convert all the donors names to upper case letters and find the length of each name (upper/ length)

	SELECT UPPER(don_name) , LENGTH(don_name) from donor ;

11.Sort the expiring date of all the bloodbags from recent to old (OrderBY ASC)

	SELECT bloodBag_Exp from bloodBags order by bloodBag_Exp ASC;

12.List all the nurses that work at the same hospital (inner join)

	SELECT nurse.nurse_name , hospital.hos_name INNER JOIN nurse on 
	hospital.hos_id = nurse.hos_id ;
 
13.Create a procedure to list receptionist that work day shift (procedure)

	create procedure
	SelectAllRep @shift varchar (20)
	as
	select * from receptionist where receptionist_shift= @shift
	GO 

EXEC SelectAllRep @shift = 'day shift';

14.Find patient names that ends with M and increase their age by 1 (where / like % / + )

	SELECT  patient_name , patient_age + 1 from patient where patient_name 
	LIKE "%M";

15.Create a procedure for all the hospitals in Istanbul (procedure)

	create procedure
	SelectAllCity @city varchar (20)
	as select * from hospital where hos_city = @city
	GO

	EXEC SelectAllCity @city = 'Istanbul';
	create procedure

