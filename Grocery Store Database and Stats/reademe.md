CREATE TABLE store (id INTEGER PRIMARY KEY, item TEXT, section TEXT, price INTEGER, popularity INTEGER);

INSERT INTO store VALUES (1, "papaya", "produce", 2.99, 50);
INSERT INTO store VALUES (2, "banana", "produce", 0.99, 95);
INSERT INTO store VALUES (3, "qtips", "hygiene", 2.99, 55);
INSERT INTO store VALUES (4, "beans", "bulk", 0.99, 50);
INSERT INTO store VALUES (5, "beyond burgers", "meat", 4.99, 65);
INSERT INTO store VALUES (6, "salsa", "fresh", 3.25, 43);
INSERT INTO store VALUES (7, "hummus", "fresh", 2.99, 35);
INSERT INTO store VALUES (8, "papaya", "hygiene", 2.99, 50);
INSERT INTO store VALUES (9, "chick'n nuggs", "meat", 4.99, 75);
INSERT INTO store VALUES (10, "peas", "frozen", 0.99, 25);
INSERT INTO store VALUES (11, "smoothie berries", "frozen", 2.99, 33);
INSERT INTO store VALUES (12, "granola", "bulk", 1.99, 80);
INSERT INTO store VALUES (13, "vitamin D", "health", 8.99,29);
INSERT INTO store VALUES (14, "nutritional yeast", "health", 2.99, 26);
INSERT INTO store VALUES (15, "popcorn", "snacks", 1.99, 47);

--display the database ordered by price. 
SELECT * FROM store
ORDER BY price desc; 

**Schema (MySQL v5.7)**

    CREATE TABLE store (id INTEGER PRIMARY KEY, item TEXT, section TEXT, price INTEGER, popularity INTEGER);
    
    INSERT INTO store VALUES (1, "papaya", "produce", 2.99, 50);
    INSERT INTO store VALUES (2, "banana", "produce", 0.99, 95);
    INSERT INTO store VALUES (3, "qtips", "hygiene", 2.99, 55);
    INSERT INTO store VALUES (4, "beans", "bulk", 0.99, 50);
    INSERT INTO store VALUES (5, "beyond burgers", "meat", 4.99, 65);
    INSERT INTO store VALUES (6, "salsa", "fresh", 3.25, 43);
    INSERT INTO store VALUES (7, "hummus", "fresh", 2.99, 35);
    INSERT INTO store VALUES (8, "papaya", "hygiene", 2.99, 50);
    INSERT INTO store VALUES (9, "chick'n nuggs", "meat", 4.99, 75);
    INSERT INTO store VALUES (10, "peas", "frozen", 0.99, 25);
    INSERT INTO store VALUES (11, "smoothie berries", "frozen", 2.99, 33);
    INSERT INTO store VALUES (12, "granola", "bulk", 1.99, 80);
    INSERT INTO store VALUES (13, "vitamin D", "health", 8.99,29);
    INSERT INTO store VALUES (14, "nutritional yeast", "health", 2.99, 26);
    INSERT INTO store VALUES (15, "popcorn", "snacks", 1.99, 47);

---

**Query #1**

    SELECT * FROM store
    ORDER BY price desc;

| id  | item              | section | price | popularity |
| --- | ----------------- | ------- | ----- | ---------- |
| 13  | vitamin D         | health  | 9     | 29         |
| 5   | beyond burgers    | meat    | 5     | 65         |
| 9   | chick'n nuggs     | meat    | 5     | 75         |
| 1   | papaya            | produce | 3     | 50         |
| 3   | qtips             | hygiene | 3     | 55         |
| 6   | salsa             | fresh   | 3     | 43         |
| 7   | hummus            | fresh   | 3     | 35         |
| 8   | papaya            | hygiene | 3     | 50         |
| 11  | smoothie berries  | frozen  | 3     | 33         |
| 14  | nutritional yeast | health  | 3     | 26         |
| 12  | granola           | bulk    | 2     | 80         |
| 15  | popcorn           | snacks  | 2     | 47         |
| 2   | banana            | produce | 1     | 95         |
| 4   | beans             | bulk    | 1     | 50         |
| 10  | peas              | frozen  | 1     | 25         |

---

[View on DB Fiddle](https://www.db-fiddle.com/)


--what is the avg price of items in the bulk section? 
SELECT AVG(price) "avg bulk item price"
FROM store
where section='bulk'; 

--what are the most 5 popular items? 
SELECT item, price, popularity
FROM store
order by popularity desc
limit 5; 
