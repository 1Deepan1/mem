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

	>Anomalies are addressed via functional dependency & nomalization

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








