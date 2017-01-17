##RDBMS [in progress]
###References:
- [DBMS by Sanjit jain](https://www.youtube.com/playlist?list=PLmXKhU9FNesR1rSES7oLdJaNFgmuj0SYV)
- [DBMS by Jennifer widom](https://www.youtube.com/playlist?list=PLLH73N9cB21WYr92CFMaE1ygwqLiBWz4I)
- [DBMS by Dan Suciu](http://courses.cs.washington.edu/courses/csep544/15au/)

---

### Data Anomalies
>Anomalies are addressed via functional dependency & normalization

1. Insertion anomaly - data is repeated
2. Update anomaly - update one item ,
   but end up updating multiple places
3. Deletion anomaly - end up deleting multiple places

---

### Functional Dependencies
- It's a tool for normalization
- Given a relation R, a set of attributes X in R is said to functionally determine another set of attributes Y, also in R, (written X → Y) if, and only if, each X value in R is associated with precisely one Y value in R; R is then said to satisfy the functional dependency X → Y.
- eg: say if state name is given , you will be able to find the country it belongs. But vice vera is not possible. 
- eg: Employee ID → Employee Name

---

### Functional Dependencies 

<small>

|name|category|color|department|price
|----|--------|-----|----------|-----
|Gizm|Gadget  |Green|Toys      |49
|Twea|Gadget  |Green|Toys      |99
|Gizm|Tools   |Green|Office Sup|49

</small>

- category --> department (category determines department)
- color,category --> price ( this is wrong )

---

### Another example

<small>

|name|category|color|department|price
|----|--------|-----|----------|-----
|Gizm|Gadget  |Green|Toys      |49
|Twea|Gadget  |Black|Toys      |99
|Gizm|Tool    |Green|Office-sup|59

</small>

- name --> color (name determines color)
- category --> department (category determines department)
- color,category --> price (color and category determines price)

---

### Closure of a set of Attributes
Example:
		
		1.Name -> Color
		2.Category -> Department
		3.Color,Category -> Price

Closures:
		
		1.name+ = {name, color}
		2.{name, category}+ = {name, color,category,department,price}
		3.color+ = {color}

---

### Keys

- Superkey  - functionally determines all other attributes
- Superkey is a set of attributes A1...An such that for any other attribute B, We have A1,...An -> B
- Candidate Key is a minimal superkey 
- Candidate Key is a superkey for which no subset is a superkey
- One of the Candidate key becomes primary key 


---

### Normalization

---

### BCNF

```
A relation R is in BCNF , whenever X -> B 
It is non trivial dependency
then X is a super key.```

Equivalently

```
In any set of attributes , if you compute closures, 
either you get same set of attributes or
you get all the attributes.

X+ = X 
X is a super key 
Trivial dependency
	or 
X+= [All the attributes] 
X is a super key 
Non Trivial dependency
```

---

### BCNF ALGORITHIM

1. Find X such that (X != X+) and (X != [All attributes])
2. If not found then R is in BCNF
3. Else
5. Decompose R into R1( X U Y ) and R2 (X U Z)
6. Normalize(R1) ; Normalize (R2 )

<img data-src="lib/pics/bcnf.png">

---

<small>

|Name|SSN 	   	 |PhoneNumber|City   |
|----|-----------|-----------|-------|
|Fred|123-34-3458|123456781  |Seattle|
|Fred|123-34-3458|223456782  |Seattle|
|Jose|223-34-3458|323456783  |WestFie|
|Jose|223-34-3458|423456784  |WestFie|

-
- SSN -> Name , City
- Key (SSN,PhoneNumber)

</small>

``` 
In other words
SSN+ = { Name , City } is neither SSN nor all the attributes
Neither X+ = X  nor X+= [All the attributes]
So decompose.

```

---

### BCNF Decmposition

<img data-src="lib/pics/bcnf-3.png">

- Y (Name,City,SSN)
- Z (SSN , Phone Number)

---

<small>

|Name|SSN 	   	 |PhoneNumber|City   |
|----|-----------|-----------|-------|
|Fred|123-34-3458|123456781  |Seattle|
|Fred|123-34-3458|223456782  |Seattle|
|Jose|223-34-3458|323456783  |WestFie|
|Jose|223-34-3458|423456784  |WestFie|

-
- SSN -> Name , City
- Key (SSN,PhoneNumber)
------
-

|Name|SSN 	   	 |City 
|----|-----------|----
|Fred|123-34-3458|Seattle


------
-

|SSN|PHONENUMBER
|---|-----------
|123-34-3458|123456781 

---


</small>

### Case Study
<small>
Mr. Frumble (who is a great character for small kids that always gets into trouble) designed a simple database to record projected monthly sales in his small store. He never took a database class, so he came up with the following schema

Sales(name, discount, month, price)

He inserted his data into the database, and then he realized that there is something wrong with it: it was difficult to update. He hires you as a consultant to fix his data management problems. He gives you this file mrFrumbleData.txt and says: "Fix it for me!". Help him by normalizing his database. Unfortunately you cannot sit down and talk to Mr. Frumble to find out what functional dependencies make sense in his business. Instead, you will reverse engineer the functional dependencies from his data instance.

[mrFrumbleData.txt](http://courses.cs.washington.edu/courses/csep544/15au/hw/hw2/hw2-data.txt)
<small>

---

1. Functional Dependencies
		Month --> Discount
		Name  --> Price
2. Closure set
		Month+ = {Month,Discount}
		Name+ = {Name,Price}
3. BCNF
		X+ = X or X+ gives all the attributes
		Funtional dependencies doesn't meet both the conditons
		So decompose..

---

<img src="lib/pics/bcnf-casestudy.png"/>
<small>

1. R1(Name,Price)
2. R2(Name,Month,Discount)

3. R2 can be decompsed into
    - R3(Name,Month)
    - R4(Month,Discount)

</small>

```
Sales(name, discount, month, price)
is decomposed into 
R1(Name,Price)
R3(Name,Month)
R4(Month,Discount)
```










		









