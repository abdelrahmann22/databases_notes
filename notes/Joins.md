## Random Table

| Sid | Sname  | Did  |
| --- | ------ | ---- |
| 1   | Ahmed  | 10   |
| 2   | Khalid | 10   |
| 3   | Eman   | 20   |
| 4   | Omar   | Null |

| Did | Dname |
| --- | ----- |
| 10  | SD    |
| 20  | HR    |
| 30  | IS    |
| 40  | Admin |

## Types of Joins
### Cross Join
**Cartesian Product**
```sql
Select Sname, Dname
From Student cross join Dept
```

| Sname  | Dname |
| ------ | ----- |
| Ahmed  | SD    |
| Khalid | SD    |
| Omer   | SD    |
| Eman   | SD    |
| Ahmed  | HR    |
| Khalid | HR    |
### Equi Join (PK =FK)
**Equi Join**
```sql
select Sname, Dname
From Student, Dept
where Dept.did = student.did
```
or
```sql
select Sname, Dname
From Student S inner join Dept D
on D.did = S.did
```

| Sname  | Dname |
| ------ | ----- |
| Ahmed  | SD    |
| Khalid | SD    |
| Eman   | HR    |

### Outer Join
##### Left Outer Join 
```sql
Select Sname, Dname
From Student S left outer join Dept D
on D.did = S.did
```

| Sname  | Dname |
| ------ | ----- |
| Ahmed  | SD    |
| Khalid | SD    |
| Eman   | HR    |
| Omer   | Null  |

##### Right Outer Join
```sql
select Sname, Dname
From Student D right outer join Dept D
On D.did = S.did
```

| Sname  | Dname |
| ------ | ----- |
| Ahmed  | SD    |
| Khalid | SD    |
| Eman   | HR    |
| Null   | IS    |
| Null   | Admin |

##### Full Outer Join
```sql
select Sname, Dname
From Student D full outer join Dept D
On D.did = S.did
```

| Sname  | Dname |
| ------ | ----- |
| Ahmed  | SD    |
| Khalid | SD    |
| Eman   | HR    |
| Omar   | Null  |
| Null   | IS    |
| Null   | Admin |
***Right + Left = Full***
### Self Join

| Eid | Ename | SuperId |
| --- | ----- | ------- |
| 1   | Ahmed | null    |
| 2   | Omar  | 1       |
| 3   | Eman  | 1       |
| 4   | Nada  | 2       |

```sql
select Ename as EmpName, Ename as SuperName
from Empolyee X, Employee Y
where Y.eid = X.SuperId
```

| Eid  | Ename |
| ---- | ----- |
| Omar | Ahmed |
| Eman | Ahmed |
| Nada | Omar  |

### Example SQL
##### Cartesian Join
```sql
Select St_fname, Dept_name
from Student Cross join Department
```

##### Equi Join
```sql
Select st_fname, dept_name
from Student inner join Department
where Department.Dept_Id = Student.Dept_Id

Select St_fname, D.* --- All Department---
From Student S inner join Department D
On D.dept_Id = S.Dept_Id and st_address = 'Alex'
Order by dept_name
```

##### Outer Join
```sql
Select St_name, Dept_name
From Student S left outer join Department D
On D.Dept_Id = S.Dept_Id

Select St_name, Dept_name
From Student S right outer join Department D
On D.Dept_Id = S.Dept_Id

Select St_name, Dept_name
From Student S full outer join Department D
On D.Dept_Id = S.Dept_Id

```

##### Self Join
```sql
Select X.St_fname as Sname, y.*
From Student X, Student Y
Where Y.St_ID = X.St_super
```

##### Join Multi Tables
```sql
select st_fname, crs_name, grade
from Student S, Stud_course SC, Course C
where S.St_id=Sc.st_id and c.Crs_id=Sc.Crs_Id
```

