SQL queries for learners---

                        CLASS 1 
select * from jashva
select empid,empsal,empname from jashvA
select empid,empname,empsal AS NEWSAL FROM jashva
select empid,empsal,empsal*10 from jashva
select empid,empsal,empsal*10 AS anualslary from jashva
ANYTHING NULL = NULL arthmatical operators
select * from jashva order by empsal desc
select * from jashva order by 2,3
                                               
											   CLASSS 2 
											   
slect * from jashva where empid =1001;
select * from jashva where empname like 'jashva'
select * from jashva where deptno!=20
select * from jashva where empsal >2000
select * from jashva where empsal >=1000
select * from jashva where deptno= 20 and job ='manager' 
select * from jashva where deptno in(10,20) and job ='clerk'
select * from jashva where job is null
select * from jashva where empsal between 2000 and 5000;
select * from jashva where empname like '_a%'
select * from jashva where empname like '____'
select * from jashva where empname like '%jash%'

                                                    CLASS 3
select * from jashva where empname like '[^a-d]%'
 select distinct deptno from jashva
 union ----it will remove duplicates,asc order 
 union all ---it wont  give the ORDER
 intersect------both table matching records
 except -----data was their in table a not their in table b
 joins
 
                                                    CLASS 4
joins

                                                  CLASS 5
inner join-------------matching records both tables                             
left join--------------all recors from left table matching  records from right table
right join ------------ all records from right table matching records from left TABLE
full outer join -------all records from left and right table  
we dont have self join saparate --- if we are join one table that is called self join
cross join ----it will multiply the records  

Round function ----select empname, round(empsal,2)as newsal from jashva
floor -------select floor(10.11)----10
ceiling function ------it means u the value--------
upper case---if it is a lower case it will converted into uppercase-----select upper('asskkn')
lower case -----if it is a uppercase it will converterd into lower case ----------select lower('HKJADKJF')
LTRIM---it will cut the spaces------select ltrim('    jhbljbad;)
RTRIM----it will cut the right of the value-----select rtrim('jashva    ')
substring------it will give the particluar value what we need--------select empid, substring(empname,1,4) from jashva
left function -----it will cut the value-------select left('asdasd',3)
right function ------it will cut he right value -------selec right('hadasd',4)
replace -------it will replace the vlaue what you need--------SELECT empid,empname,replace(job,'manager','gm')from jashva
                                                   CLASS 6

charindex-----it will gives possition of a particluar string-----select charindex('s','jashva',1)
how to find a empmail--
select substring(empmail,1,charindex('@',empmail)-1),SUBSTRING
(empmail,charindex('@',empmail,1)+1,len(empmail)),empmail from harikumar
	
select substring(empmail,1,charindex('@',empmail)-1),
substring(empmail,charindex('@',empmail,1)+1,len(empmail)),empmail  from jashva
how get date------select getdate()
if you are see last 10 date -----select getdate()-10
if we are see after 5 days date ------------select getdate ()+5
how to see todays year ------select year(getdate())
how to see month in this year-----select month (getdate())
how wil see th today--------select day(getdate())
who joind in a 2023-----------select * from jashva where year(joindate)=2023
who join in a feb month----------select * from jashva where month(joindate)=5
who join in a 16 day ----------select * from jashva where day(joindate)=16
how to see hours-------select datepart(hh,getdate())
how to see first quater join in 2023 year-----select * from jashva where datepart(qq,joindate)=1 and year(joindare)=2023
how to see last 10 days sales----------select * from jashva where joindate>=getdate()-10s
how to see day in the month ------- select * from jashva where datename(dw,joindate)=saturday
how to see the monthe of year ------select * from jashva where datename(mm,joindate)=january 
rank--it will give skip value----select *,rank()over(order by empid) from jashva
DENSE_RANK-------it will continue the value-------select *,dense_rank()over(order by empsal desc) from jashva 
rownumber---------it will givw rownumber---select *,row_number()over(order by empid desc) from jashva
ntile-------it will give the a group of the table into divrd--------select *,ntile(2)over(order by empsal desc) from jashva

                                             CLASS 7
how to increase the one department 5% incrment slary another depatment 10% salary increments

select *,
case when deptno =10 then empsal+empsal*5/100
     when deptno = 20 then empsal+empsal*10/100
	  else empsal end as newsal from jashva
	  
how to see null ina table --------select * from jashva where empsal is null;
how to add commession and salary via using is null--------select empid,empsal,empsal+isnull(commession,0)from jashva
coalesce---this function will give skip the null value-------
cast------------it will convert the data TYPE
convert ---------it will convert the string into VARCHAR 

                                    CLASS 8
								
how to see max of empsal in table-----------------select max(empsal)from jashva
how to see min of empsal in table-----------------select min(empsal)from jashva
how to see avgof empsal in table------------------select avg(empsal)from jashva
how to see count in table ---------------select count(*)from jashva
ALL THE AGGRATION FUNCTION WILL IGNORE NULL VALUES
how to max sal emp see all data---------select * from jashva where empsal =(select max(empsal)from jashv)
how to see deptno wise count ----------select deptno,count(*)from jashva group by deptno
year wise how many employes joined -------select year(joindate) count(*)from jashva group by year(joindate)
what is the difference b/w  where clause and having clause---
where clause will use the normal data
having cluse will use the aggrated data
                                                        
                                  CLASS 9
select max(empsal)from jashva
select * from jashva where = (select max(empsal)from jashva
 how to find 2 nd highest salary ----select * from jashva where =(select max(empsal)from jashva where >(select max(empsal)from jashva))
how to find 5 th salary -----
select *from (
select *,dence_rank()over(order by empsal desc)as jash from jashva)a  where jash=5

 how to find deptno wise 3 rd highest salary------
select *from (
select *,dence_rank()over(partition by deptno order by empsal desc)as jash from jashva)a  where jash=3
                                                    CLASS 10
													
how to do with out join the tables 
select * from jashva where deptno not in(select  distinct deptno from emp)

how to do backup the data--------------select *into newtable from oldtable 
how to do with out create statement create table ------------select *into newtable from oldtable 
how to create table with ou create statement --------------select * inot newtable from oldtable where 1=2-----------any false condition


                                                           
														  CLASS 11
DDL statements-------create,alter,DROP
create -- create table jashva (empid number,empname varchar(20),empsal int)
alter --- alter table add emploation varchar(30)
Drop --- drop table jashva --
drop column ----- alter table jashva drop emplocation

DML---- statements --- select,insert ,update,DELETE
select --select * from jashva
insert ----insert into jashva values (101,'hari',1000)
update --- update jashva set empname='harikumar' where empsal =101
delete -----delete from jashva -------it will delete only data
delete ----delete from jashva where empsal=2000
how we can do insert into one table to another table ---- we can use joins also		
insert newtable select * from jashva



                                                         CLASS 12
updatae all emplores slary -----------update jashva set empsal =5000-- it will effect alla emplyes
how to do multiple records update ----update jashva set empsal =2000,empname ='hosanna',emplocation ='blr' where empsal = 101
how we can do 10 int 20 s inot 20 inot 10  s-------update jashva set empid = case when empid=10 then 20
																				  when empid=20 the 10 end
																				 
DDL---create,alter,drop,truncate,	 table,views,synnonyms,prcedures,functons
create ----integer,string,varchar(20),date,float

                                                  CLASS 13
												  
how to see in system how many table is their -----select * from sys.tables
how to increase  the data type--------alter table harikumar alter column job varchar(50)
hoe to decrise the data type------------alter table harikumar alter column job varchar(20)
how to drop column ---alter table jashva drop column 
how to drop table ----drop table jashva
how we can ceate computed column ----create table mpl(empid  int,empcommessiom int,empal as empid*empcommession)------it will work arthamatical operations
waht is identity column--- it will ganarate the automatic number  --create table(empid int identity (1,1),empsal int)
what id differenc b/w delete and truncate
delete -----we can delete row by row and fully or parcially
truncate-----it means only table level we can delete
log table---log table will maintain all historical data


                                            CLASS 14
how to get half records in a table -----select top 50 percent * from harikumar 
how to select duplicates in a table ----select empid,count(*)from harikumar group by empsal having count(*)>1
how to remove duplicates-----;with jashva as(select*,ROW_NUMBER()over(order by empsal asc)as jash from harikumar delete from jashva where jash>1

                                          CLASS 15
CONSTRAINTS
not null---it means it wont allow nulls---create table emp(empid int not null,empsal int)
check CONSTRAINTS -- it wil check the values ------create table emp(empage int CONSTRAINTS myage check(age between 1 and 90)
default ---if you are not giving number it will take default number----create table emp(empjoindate date default getdate()
unique key ----it will remove duplicate--create table emp(empid int unique
primary key---i wont allow dulicate ---create table student (rno unt primary key)
foreign key --it will allow nulld and duplicates--it based on the paimary table referrence as a parent table
 
 create table result(hno int,marks int foreign key (hno) references student(rno))
  create table student(rno int primary key,studentname varchar(60),dob date)

create table result (hno int,marks int,foreign key(hno) references student(rno))

select * from student

select * from result

insert into result  values(101,50)

insert into sudent(101,'jashva','2022-08-20')

                                                 CLASS 16
delete ---when we delete the foreign key before we can delete the primry key 	
if we created primary key automatically index got created
Indexes ---are special lookup tables that need to be used by the database search engine to speed up data retrieval
Clustered ---------indexes sort and store the data rows in the table or view based on their key values.
normalization---it wil spilent the TABLESPACE
denor,alization----it means it will combained the tables
user defind schema----A Schema in SQL is a collection of database objects associated with a database.

                                              CLASS 17
											  
view--stored selet query--create view viewname as old table 
we can use jois also----we can update also but it will affect base table also
alter view--we can alter view---alter view viewnmae as old table
sp_helptext hari_view----view details
complex view---complex view is a aggregtions we can do---we cannt update 
meterialized views -is a refresh the data auto maticallly --
how to one company wise sales amount---select substring(companyname,1,9) as newsal	,sum(sales)from ambani group by substring(companyname,1,9)
synonym--synonym is a ypu are their in one data base but you can see in your table another data based
select * from [master].[dbo].harikumar---fully qualified name
create synonym jash for [master].[dbo].harikumar----synonym creating
select * from  jash---synonym name

                                                    CLASS 18
													
variables-global variables --to store some value into the table
          - local variables --
select @@VERSION--currently we are using version 
select @@servername- to see server name
how we can see erroe -------select * from harikumar select @@error
select ---rowcount---select @@reowcount
what is declare --The DECLARE statement initializes a Transact-SQL variable  
Declare condition ---  declare @a int
                       declare @b varchar(40)
                       set @a =10
                       select @a
					   
how to do variables aggrations --
declare @a int,
@b int,@c int
set @a=10
set @b=20
set @c=@a+@b 
print @c

 how Declare variables we can use if condition
 
 declare @a int,@b int
set @a=100
set @b=sqrt(@a)
if @b*@b=@a
print'it is a suitsble'
else
print'it is not perfect'

while loop cindition -------The while loop in SQL begins with the WHILE keyword followed by 
                            the condition which returns a Boolean value i.e. True or False.
							
temporary  table --- we dont have a temp table on top taht we can create  tem table   like------with condition 	

simple temporary table----create table #emp(empid int)


                                                 CLASS 19
we cau use incremantal load in SP
												 
												 
												 goutham -----new password snoeflake------Goutham@123
