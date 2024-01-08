
![Netflix logo](https://github.com/antonionunnally/SQL/assets/97487571/e0c53dd6-6d28-4e3e-b83b-80f8ccdd7ed0)
# This project reveals insights about TV and Movie content hosted on Netflix. 

## The project was written using the PostgreSQL dialect and utilized data from the following two Netflix datasets:

**Query #1** How many movie titles are there in the database? (movies only, not tv shows)

    select count(*) 
    FROM "netflix_titles_info"
    WHERE type='Movie';

| count |
| ----- |
| 8     |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)
