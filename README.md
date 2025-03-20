# Pickle Ball Club Relational Database

- The task is to model and build a relational database for a pickleball club. This club offers lessons, has various levels of memberships, allows court reservations, and participates in tournaments. Our goal is to precisely model these relationships, create sample data, and populate the entities and their attributes accordingly. We aim to execute functional queries on this data to gain valuable business insights into the club and its activities. 

## Authors
**MIST 4610 Section #47114 Group 3**
- [Kennedy Hankinson](https://www.github.com/kennedyhankinson)
- [Johnny Vo](https://www.github.com/jvjohnny99)
- [Andrew Bowman](https://www.github.com/andrewbowmn)
-  Charlie Nelson
- [Sneha Neelagaru](https://www.github.com/sneelagaru03)
## Data Model

![Data Model](https://raw.githubusercontent.com/andrewbowmn/4610project1/main/datamodel.png)

- In the pickleball club, members are able to take many lessons. Coaches are able to teach many lessons, and as a result, members that take multiple lessons may have multiple coaches. Members are also allowed to reserve a court throughout the year, and the same courts can be reserved multiple times. Each member is associated with only one membership, and each membership is associated with only one payment. A member of the club can be a tournament participant. Participants can compete in multiple tournaments, and tournaments can have multiple participants. These participants have game results that relate to the tournament they participated in.



## Data Dictionary



>Table: Coach

| Column Name      | Description                                                   | Data Type | Size | Format | Key? |
|------------------|---------------------------------------------------------------|-----------|------|--------|------|
| coachID          | Unique sequential number indicating the identification of the coach | Int       | 2    |        | PK   |
| coachFirstName   | Coach’s first name                                            | Text      | 10   |        |      |
| coachLastName    | Coach’s last name                                             | Text      | 14   |        |      |
| coachLevel       | Coach’s personal skill level                                  | Text      | 10   |        |      |
| coachAvailability| Coach’s availability                                          | Text      | 20   |        |      |

>Table: Court

| Column Name    | Description                                           | Data Type | Size | Format | Key? |
|----------------|-------------------------------------------------------|-----------|------|--------|------|
| courtID        | Unique sequential number indicating the identification of the court | Int       | 3    |        | PK   |
| courtNumber    | Court’s physical sign number at location              | Text      | 2    |        |      |
| courtSurface   | Material that the court is made of                    | Text      | 10   |        |      |
| courtLocation  | Location of court at fields                           | Text      | 10   |        |      |
| courtStatus    | Availability of court                                  | Text      | 14   |        |      |

>Table: Lesson

| Column Name    | Description                                           | Data Type | Size | Format   | Key? |
|----------------|-------------------------------------------------------|-----------|------|----------|------|
| memberID       | Unique sequential number indicating the identification of the member | Int       | 3    |          | PK, FK (ref. Member) |
| coachID        | Unique sequential number indicating the identification of the coach | Int       | 2    |          | PK, FK (ref. Coach)  |
| lessonDateTime | Start date of the lesson                               | Date      | 14   | 9999-99-99 99:99:99 |      |
| lessonDuration | Duration of the lesson                                 | Text      | 10   |        |      |
| lessonFocus    | Main objective of lesson                               | Text      | 18   |        |      |

>Table: Member

| Column Name        | Description                                                       | Data Type | Size | Format         | Key? |
|--------------------|-------------------------------------------------------------------|-----------|------|----------------|------|
| memberID           | Unique sequential number indicating the identification of the member | Int       | 3    |                | PK   |
| memberFirstName    | Member’s first name                                               | Text      | 15   |                |      |
| memberLastName     | Member’s last name                                                | Text      | 15   |                |      |
| memberEmail        | Member’s email address                                            | Text      | 30   |                |      |
| memberPhoneNumber  | Member’s phone number                                             | Text      | 10   | 999-999-9999    |      |
| memberType         | Member’s category depending on if they are a new member or a senior member | Text      | 15   |                |      |
| memberSkill        | Skill level of member                                            | Text      | 10   |                |      |
| memberJoinDate     | Date that member joined the club                                 | Date      | 8    | 9999-99-99     |      |
| membershipID       | Unique sequential number indicating the identification of the membership | Int       | 3    |                | FK (ref. Membership) |

>Table: Membership

| Column Name        | Description                                                       | Data Type | Size | Format   | Key? |
|--------------------|-------------------------------------------------------------------|-----------|------|----------|------|
| membershipID       | Unique sequential number indicating the identification of the membership | Int       | 3    |          | PK   |
| membershipName     | Name of the membership that pertains to the member                | Text      | 10   |          |      |
| membershipPrice    | Price of the membership                                           | Text      | 3    |          |      |
| membershipDuration | Length of the membership                                          | Text      | 10   |          |      |
| membershipBenefits | Perks/benefits of having the membership                           | Text      | 25   |          |      |
| paymentID          | Unique sequential number indicating the identification of the payment of the membership | Int       | 3    |          | FK (ref. Payment) |


>Table: Participant

| Column Name            | Description                                                    | Data Type | Size | Format | Key? |
|------------------------|----------------------------------------------------------------|-----------|------|--------|------|
| participationID         | Unique sequential number indicating the identification of the participant | Int       | 3    |        | PK   |
| participationDivision   | Division of tournament that participant participated in       | Text      | 20   |        |      |
| participationPlacement  | Placement of participant in the tournament                    | Text      | 15   |        |      |
| memberID               | Unique sequential number indicating the identification of the member | Int       | 3    |        | FK (ref. Member) |

>Table: Payment

| Column Name    | Description                                                   | Data Type | Size | Format     | Key? |
|----------------|---------------------------------------------------------------|-----------|------|------------|------|
| paymentID      | Unique sequential number indicating the identification of the payment of the membership | Int       | 3    |            | PK   |
| paymentAmount  | Payment amount made                                           | Int       | 3    |            |      |
| paymentDate    | Date that payment was made                                    | Date      | 8    | 9999-99-99 |      |
| paymentMethod  | Method in which payment was made                              | Text      | 15   |            |      |

>Table: Reservation

| Column Name         | Description                                                    | Data Type | Size | Format         | Key? |
|---------------------|----------------------------------------------------------------|-----------|------|----------------|------|
| memberID            | Unique sequential number indicating the identification of the member | Int       | 3    |                | PK, FK (ref. Member) |
| courtID             | Unique sequential number indicating the identification of the court | Int       | 3    |                | PK, FK (ref. Court)  |
| reservationDateTime | Exact date and time of reservation                            | Text      | 14   | 9999-99-99 99:99:99 |      |
| reservationDuration | Duration of reservation                                        | Text      | 10   |                |      |

>Table: Results

| Column Name         | Description                                                    | Data Type | Size | Format | Key? |
|---------------------|----------------------------------------------------------------|-----------|------|--------|------|
| participant1ID      | Unique sequential number indicating the identification of the 1st participant in a game | Int       | 3    |        | PK, FK (ref. Participant) |
| tournamentID        | Unique sequential number indicating the identification of the tournament | Int       | 3    |        | PK, FK (ref. Tournament)  |
| participant2ID      | Unique sequential number indicating the identification of the 2nd participant in a game | Int       | 3    |        | PK, FK (ref. Participant) |
| participant1Score   | 1st participant’s score                                       | Text      | 3    |        |      |
| participant2Score   | 2nd participant’s score                                       | Text      | 3    |        |      |
| winner              | Winner of the game                                            | Text      | 3    |        |      |

>Table: Tournament

| Column Name       | Description                                                   | Data Type | Size | Format   | Key? |
|-------------------|---------------------------------------------------------------|-----------|------|----------|------|
| tournamentID      | Unique sequential number indicating the identification of the tournament | Int       | 2    |          | PK   |
| tournamentName    | Name of tournament                                            | Text      | 20   |          |      |
| tournamentDate    | Season of tournament                                          | Text      | 10   |          |      |
| tournamentFee     | Cost to participate in tournament                             | Num       | 3    |          |      |
| tournamentPrize   | Cash prize for winning tournament                             | Num       | 4    |          |      |


## Queries
#### Simple
>Provide a list of all members who have taken lessons at the club. (Q1)
```sql
SELECT DISTINCT M.memberID, M.memberFirstName, M.memberLastName
FROM Member M
JOIN Lesson L ON M.memberID = L.memberID;
```
| memberID | memberFirstName | memberLastName |
|----------|-----------------|----------------|
| 31       | Chloette        | Farries        |
| 70       | Leonie          | Jobling        |
| 115      | Marshal         | Tinto          |
| 123      | Alejoa          | Lovegrove      |
| 131      | Dix             | Sizeland       |

- This query lists all unique members who have taken lessons at the club. It joins the Member and Lesson tables on the memberID field. The DISTINCT keyword ensures that each member appears only once, even if they’ve taken multiple lessons. The result includes the member's ID, first name, and last name.

- This query helps managers identify members who are actively participating in lessons, which is key to understanding engagement. By knowing who is taking lessons, managers can offer targeted promotions to increase member retention. It also aids in operational planning by showing the demand for lessons, helping allocate resources like coaches and facilities. 

>Find the total amount of payments that have been made for memberships (Q2)
```sql
SELECT SUM(p.paymentAmount) AS totalMembershipRevenue
FROM Payment p
JOIN Membership m ON p.paymentID = m.paymentID;
```
| totalMembershipRevenue |
|------------------------|
| 53423                  |

- This query takes a sum of all the recorded payment amounts and joins the Payment and Member tables on the paymentID field to ensure payments are related to membership costs.

- This query allows the pickleball club management to have an idea of their revenue. Gross revenue is important to keep track of when running a business because it allows the club to allocate funds properly to tournament entry fees, coach salaries, court maintenance, and see what is making the most money.
- Note: Payments have minimum balance of 100, but partial payments are allowed. This query can help identify if the payments recieved do not meet the expected amount of income per membership plans.

>Display the distribution of membership tiers (and their respective prices) at the pickelball club. (Q3)
```sql
SELECT m.membershipName, COUNT(*) AS membershipCount, m.membershipPrice
FROM Membership m
JOIN Member mem ON m.membershipID = mem.membershipID
GROUP BY m.membershipName, m.membershipPrice;
```
| membershipName | membershipCount | membershipPrice |
|----------------|-----------------|-----------------|
| Silver         | 54              | 200             |
| Bronze         | 53              | 100             |
| Gold           | 47              | 300             |
| Platinum       | 46              | 400             |

- This query counts the number of members in each membership type and displays the membershipName, the total number of members in each type (membershipCount), and the price for each membership type (membershipPrice). It joins the Membership table with the Member table using the membershipID field to link each member to their membership type. The query groups the results by membershipName and membershipPrice to get the count of members for each specific membership type.
- This query helps managers understand the distribution of members across different membership types and their associated prices. It provides insights into the popularity of each membership tier, allowing managers to adjust pricing, marketing, and resource allocation accordingly. Additionally, it helps forecast potential revenue from each membership category.

>Provide the count of total tournament participants. (Q4)
```sql
SELECT COUNT(DISTINCT p.participationID) AS totalParticipants
FROM Participant p;
```
| totalParticipants |
|-------------------|
| 200               |

- This query retrieves the total number of unique participants in all tournaments. It counts the distinct participationID from the Participant table, ensuring that each participant is counted only once, even if they participated in multiple tournaments.
- Knowing the total number of participants helps in understanding the popularity and engagement in tournaments. This information is essential for event planning, resource allocation, and potentially adjusting marketing strategies to encourage more participation.


#### Complex
>Provide a list of coaches who have coached more than 5 lessons. (Q5)
```sql
SELECT C.coachID, C.coachFirstName, C.coachLastName, COUNT(L.coachID) AS totalLessons
FROM Coach C
JOIN Lesson L ON C.coachID = L.coachID
GROUP BY C.coachID, C.coachFirstName, C.coachLastName
HAVING COUNT(L.coachID) > 5;
```
| coachID | coachFirstName | coachLastName | totalLessons |
|---------|----------------|---------------|--------------|
| 1       | Diego          | Putt          | 6            |
| 2       | Kermit         | Del Castello  | 8            |
| 3       | Gothart        | Espinel       | 7            |
| 5       | Nicola         | Thyer         | 9            |
| 6       | Claudell       | Baud          | 11           |

- Add plain english description
- This query allows the pickleball club to see which coaches are most active in teaching lessons. It helps management understand which coaches are putting in the most work and generating the most value for the club. This information is useful for decisions about raises, bonuses, scheduling, or seeing if a coach needs to be assigned more lessons.

>Find club members who have not made a court reservation (Q6)
```sql
SELECT M.memberID, M.memberFirstName, M.memberLastName
FROM Member M
LEFT JOIN Reservation R ON M.memberID = R.memberID
WHERE R.memberID IS NULL;
```
| memberID | memberFirstName | memberLastName |
|----------|-----------------|----------------|
| 1        | Marty           | Crooke         |
| 2        | Friedrick       | Kimmince       |
| 3        | Jaimie          | Bess           |
| 4        | Terese          | Aireton        |
| 8        | Wilbur          | Scryne         |
- Add plain english description
- This query allows the pickleball club to see which members are not using the courts at all. It helps management figure out which members might be losing interest or are not taking advantage of their membership benefits. The club can use this information to reach out, re-engage these members, or offer incentives to get them back on the courts. Keeping members active is important for retention and making sure everyone gets value from their membership.

>Provide a list of members who have payed more than the average membership price. (Q7)
```sql
SELECT M.memberID, M.memberFirstName, M.memberLastName, MS.membershipPrice
FROM Member M
JOIN Membership MS ON M.membershipID = MS.membershipID
WHERE MS.membershipPrice > (SELECT AVG(membershipPrice) FROM Membership);
```
| memberID | memberFirstName | memberLastName | membershipPrice |
|----------|-----------------|----------------|-----------------|
| 38       | Griswold        | Bartholomieu   | 300             |
| 21       | Giustina        | Richardon      | 300             |
| 92       | Danie           | Freschini      | 400             |
| 46       | Layla           | Stote          | 400             |
| 45       | Bev             | Royle          | 400             |

- Add plain english description
- This query helps the pickleball club identify high-value members who are contributing in the top 50%. These members are likely more engaged and might be interested in premium services, loyalty perks, or exclusive events. The club should market more to these high paying customers.

#### Notes & Assumptions
- For clarity and conciseness, queries were ran and results displayed with `LIMIT 5;`
- The pickle ball club is proud to be open 24/7 for its members
- Tournaments occur once per season, for a total of 4 a year.
## Database Information
Access our database! ``al_Group_47114_G3`` on terry codrus server.

