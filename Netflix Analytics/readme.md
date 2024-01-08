
![Netflix logo](https://github.com/antonionunnally/SQL/assets/97487571/e0c53dd6-6d28-4e3e-b83b-80f8ccdd7ed0)
# This project reveals insights about TV and Movie content hosted on Netflix. 

## The project was written using the PostgreSQL dialect and utilized data from the following two Netflix datasets:

### SQL Queries


**Query #1** How many movie titles are there in the database? (movies only, not tv shows)

    select count(*) 
    FROM "netflix_titles_info"
    WHERE type='Movie';

| count |
| ----- |
| 8     |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)


---

**Query #2** When was the most recent batch of tv shows and/or movies added to the database? 

    select max(date(date_added))
    FROM "netflix_titles_info";

| max                      |
| ------------------------ |
| 2021-09-25T00:00:00.000Z |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)

---

**Query #3** List all the movies and tv shows in alphabetical order. 

    select title
    FROM "netflix_titles_info"
    ORDER BY title asc;

| title                                               |
| --------------------------------------------------- |
| Bangkok Breaking                                    |
| Blood & Water                                       |
| Confessions of an Invisible Girl                    |
| Crime Stories: India Detectives                     |
| Dear White People                                   |
| Dick Johnson Is Dead                                |
| Europe's Most Dangerous Man: Otto Skorzeny in Spain |
| Falsa identidad                                     |
| Ganglands                                           |
| Intrusion                                           |
| Jaguar                                              |
| Jailbirds New Orleans                               |
| Je Suis Karl                                        |
| Kota Factory                                        |
| Midnight Mass                                       |
| My Little Pony: A New Generation                    |
| Sankofa                                             |
| The Great British Baking Show                       |
| The Starling                                        |
| Vendetta: Truth  Lies and The Mafia                 |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)

**Query #4** Who was the Director for the movie The Starling? 

    select 
    director
    FROM "netflix_titles_info" titles
    LEFT JOIN "netflix_people" people
    ON titles.show_id=people.show_id
    where titles.title='The Starling';

| director       |
| -------------- |
| Theodore Melfi |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)

**Query #5** What is the oldest movie in the database and what year was it made? 

    select title, release_year
    FROM "netflix_titles_info"
    WHERE type='Movie'
    ORDER BY release_year asc
    LIMIT 1;

| title   | release_year |
| ------- | ------------ |
| Sankofa | 1993         |

---

[View on DB Fiddle](https://www.db-fiddle.com/f/sSnm6noFqCmtM6LJJqfwC9/0)
