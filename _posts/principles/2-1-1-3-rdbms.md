##RDBMS [in progress]
###References:
- [DBMS by Sanjit jain](https://www.youtube.com/playlist?list=PLmXKhU9FNesR1rSES7oLdJaNFgmuj0SYV)
- [DBMS by Jennifer widom](https://www.youtube.com/playlist?list=PLLH73N9cB21WYr92CFMaE1ygwqLiBWz4I)
- [DBMS by Dan Suciu](http://courses.cs.washington.edu/courses/csep544/15au/)


---

### Topics
- Functional Dependencies
- Normalization
- Case Study on Normalization
- Trasaction & Isolation 

---

### Data Anomalies

- Three kinds.
	1. Redundancy anomaly - data is repeated
	2. update anomaly - update one item , but end up updating multiple places
	3. Deletion anomaly - end up deleting multiple places

	>Anomalies are addressed via functional dependency & normalization

---

### Functional Dependencies
- It's a tool for normalization
- Given a relation R, a set of attributes X in R is said to functionally determine another set of attributes Y, also in R, (written X → Y) if, and only if, each X value in R is associated with precisely one Y value in R; R is then said to satisfy the functional dependency X → Y.
- a is funtionally dependent on b , if given a , you should be able to find b.
- eg: say if state name is given , you will be able to find the country it belongs. But vice vera is not possible. 
- eg: Employee ID → Employee Name

---

### Functional Dependencies 

|name|category|color|department|price
|----|--------|-----|----------|-----
|Gizm|Gadget  |Green|Toys      |49
|Twea|Gadget  |Green|Toys      |99

- name --> color (name determines color)
- category --> department (category determines department)
- color,category --> price (color and category has different set of price) this is wrong

---

### Another example

|name|category|color|department|price
|----|--------|-----|----------|-----
|Gizm|Gadget  |Green|Toys      |49
|Twea|Gadget  |Black|Toys      |99
|Gizm|Tool    |Green|Office-sup|59

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

- Which functionally determines all other attributes
- Superkey is a set of attributes A1...An such that for any other attribute B, We have A1,...An -> B
- Key is a minimal superkey 
- A superkey for which no subset is a superkey

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
In any set of attributes , if u compute closures, 
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
4. Let Y = (X+) + X  and Z = [All Attributes] - (X+)
5. Decompose R into R1( X U Y ) and R2 (X U Z)
6. Normalize(R1) ; Normalize (R2 )

<img data-src="lib/bcnf.png">

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

<img data-src="lib/bcnf-3.png">

- Let Y = (X+) + X  and Z = [All Attributes] - (X+)
- Y (Name,City,SSN)
- Z (SSN , Phone Number)

---

### BCNF Decompostion
Y

|Name|SSN 	   	 |City 
|----|-----------|----
|Fred|123-34-3458|Seattle
|Jose|223-34-3458|WestFie


------
Z

|SSN|PHONENUMBER
|---|-----------






		









