##### isnull
```sql
select isnull(st_fname, 'any string') as NewName
from student
```

Replaces the null with any string and can replace it with another column.

```sql
select isnull(st_fname. st_lname) as NewName -- we need to make alice because it's new column --
from student
```

##### coalesce
it function for multiple replacement if the another function is still null
```sql
select coalesce(st_fname, st_lname, st_address)
from student
```
It's alternative for isnull.

##### convert
```sql
select st_fname+' '+convert(varchar(2), st_age)
from student
```
Convert the different data type to the specific data type to concatenate .

##### concat
```sql
select isnull(st_fname, '') + ' ' +convert(varchar(2), isnull(st_age, 0))
from student
```
It's a lot of function and it will affect the performance so we have another function called concat.

```sql
select concat(st_fname,' ', st_age)
from Student
```
It convert automatically the datatypes and also remove any null and replace it with blank string.

##### Like
```sql 
select *
from Student
where st_fname = 'ahmed'
```
Use `=` for exact matches (e.g., `st_fname = 'ahmed'`).

```sql
select *
from student
where st_fname like 'ahm%' --- get all names that starts with ahm and enc with any characters
```
Use `LIKE` for pattern matching (e.g., `st_fname LIKE 'ahm%'` to find names starting with `'ahm'`).
```sql
_ one Char
% zero or More Char
```
Examples
```sql
select *
from Student
where st_fname like '_a%' -- get any name that starts with any char and after it 'a' follows with any chars--
```

```sql
'a%h' --- string starts with a and ends with h ---
'%a_' --- string before the end 'a' ---
'ahm%' --- starts with with 'ahm' ---
'[ahm]%' --- string starts with 'a' or 'h' or 'm' ---
'[^ahm]%' --- string doesn't start with 'a' or 'h' or 'm' ---
'[a-h]%' --- range, starts with any char between 'a' to 'h' ---
'[^a-h]%' --- doesn't start with this range ---
'[346]%' --- starts with 3 or 4 or 6 ---
'%[%]' --- string ends with '%' ---
'%[_]%' --- string _ in between 'ahmed_ali'
'[_]%[_]' --- starts with _ and ends with _ '_ahmed_'
```


##### order by
```sql
select st_fname, dept_id, st_age
from Student
order by 1
```
Order by the first column.

```sql
select st_fname, dept_id, st_age
from Student
order by dept_id asc, st_age desc
```
This SQL query retrieves `st_fname`, `dept_id`, and `st_age` from the `Student` table, sorting the results **first by `dept_id` in ascending order** and **then by `st_age` in descending order**. It groups students by department and lists older students first within each department.