#1. Give me a list of users who have logged meals
select
DISTINCT ts.UserId,
p.FirstName,
p.LastName,
CONCAT(p.FirstName, ' ' , p.LastName) as 'Full Name',
p.email,
p.DateofBirth,
DATEDIFF(yy, DateofBirth, GETDATE()) as Age,
p.Gender,
case 
    when P.Gender = '1' then 'Male'
    when P.Gender = '2' then 'Female'
    when P.Gender = 'Male' then 'Male'
    else 'Female' 
    End AS 'Gender Update',
p.MealScore as 'User''s Meal Score',
p.LastAction,
mt.MealTypeName,
m.Created,
m.MealScore as 'Total Daily Score Per Meal',
CASE
                WHEN (m.MealScore IS NOT NULL) and (m.MealScore != 0) THEN  
                        CASE
                            WHEN m.MealScore <= p.MealScore THEN 
                                CASE 
                                        WHEN p.MealScore <= 12 THEN 
                                            CASE 
                                                WHEN m.MealScore = p.MealScore THEN 'GREEN' 
                                                WHEN m.MealScore <= (p.MealScore - 2) THEN 'RED' 
                                                WHEN m.MealScore = (p.MealScore -1) THEN 'YELLOW'
                                                ELSE 'RED'
                                            END
                                        ELSE
                                            CASE 
                                                WHEN (m.MealScore = p.MealScore) OR (m.MealScore = (p.MealScore -1)) THEN 'GREEN'
                                                WHEN m.MealScore = (p.MealScore - 2) THEN 'YELLOW'
                                                WHEN m.MealScore <= (p.MealScore -3) THEN 'RED'
                                                ELSE 'RED'
                                            END
                                    END
                            ELSE 'RED'        
                        END 
                ELSE 'GRAY'
            END AS 'Food Score Key',
mmi.updated,
mmi.ImportScore,
mi.IsFavorite, 
fi.Name as 'Brand(Name)',
fi.Brand,
fi.ServingSize
FROM ThriveSubscriptionItems ts 
join Patients p on p.Id = ts.UserId
join Meals m on m.UserId = p.Id
join MealTypes mt on m.MealTypeId = mt.Id
Join MealMealItems mmi on m.Id = mmi.MealId
join MealItems mi on mmi.MealItemId = mi.Id
join FoodItems fi on mi.fooditemid = fi.id
--where p.FirstName = 'Antonio'
order by created desc

#2. Meal Count User Stats
SELECT p1.id,p1.FirstName, p1.LastName, 
CONCAT(p1.FirstName, ' ' , p1.LastName) as 'Full Name', COUNT(*) as total_meals,
CASE
        WHEN COUNT(*) > 15 THEN 'Active'
        WHEN COUNT(*) BETWEEN 7 AND 15 THEN 'Moderate'
        WHEN COUNT(*) < 7 THEN 'Non-Active'
    END as "App Engagement Status"
FROM Patients p1
JOIN Meals m on p1.id = m.userid
--where CreateDate >= DATEADD(day, -30, getdate())
group by p1.id, p1.FirstName, p1.LastName
