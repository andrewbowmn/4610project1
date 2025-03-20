
# 4610 Group 3: Pickle Ball Club

- The task is to model and build a relational database for a pickleball club. This club offers lessons, has various levels of memberships, allows court reservations, and participates in tournaments. Our goal is to precisely model these relationships, create sample data, and populate the entities and their attributes accordingly. We aim to execute functional queries on this data to gain valuable business insights into the club and its activities. 

## Authors

- [Kennedy Hankinson](https://www.github.com/kennedyhankinson)
- [Johnny Vo](https://www.github.com/jvjohnny99)
- [Andrew Bowman](https://www.github.com/andrewbowmn)
-  Charlie Nelson
- [Sneha Neelagaru](https://www.github.com/sneelagaru03)
## Data Model

![Data Model](https://raw.githubusercontent.com/andrewbowmn/4610project1/main/datamodel.png)

- In the pickleball club, members are able to take many lessons. Coaches are able to teach many lessons, and as a result, members that take multiple lessons may have multiple coaches. Members are also allowed to reserve a court throughout the year, and the same courts can be reserved multiple times. Each member is associated with only one membership, and each membership is associated with only one payment. A member of the club can be a tournament participant. Participants can compete in multiple tournaments, and tournaments can have multiple participants. These participants have game results that relate to the tournament they participated in.



## Data Dictionary



Table: Coach

| Column Name      | Description                                                   | Data Type | Size | Format | Key? |
|------------------|---------------------------------------------------------------|-----------|------|--------|------|
| coachID          | Unique sequential number indicating the identification of the coach | Int       | 2    |        | PK   |
| coachFirstName   | Coach’s first name                                            | Text      | 10   |        |      |
| coachLastName    | Coach’s last name                                             | Text      | 14   |        |      |
| coachLevel       | Coach’s personal skill level                                  | Text      | 10   |        |      |
| coachAvailability| Coach’s availability                                          | Text      | 20   |        |      |

Table: Court

| Column Name    | Description                                           | Data Type | Size | Format | Key? |
|----------------|-------------------------------------------------------|-----------|------|--------|------|
| courtID        | Unique sequential number indicating the identification of the court | Int       | 3    |        | PK   |
| courtNumber    | Court’s physical sign number at location              | Text      | 2    |        |      |
| courtSurface   | Material that the court is made of                    | Text      | 10   |        |      |
| courtLocation  | Location of court at fields                           | Text      | 10   |        |      |
| courtStatus    | Availability of court                                  | Text      | 14   |        |      |

### Table: Lesson

| Column Name    | Description                                           | Data Type | Size | Format   | Key? |
|----------------|-------------------------------------------------------|-----------|------|----------|------|
| memberID       | Unique sequential number indicating the identification of the member | Int       | 3    |          | PK, FK (ref. Member) |
| coachID        | Unique sequential number indicating the identification of the coach | Int       | 2    |          | PK, FK (ref. Coach)  |
| lessonDateTime | Start date of the lesson                               | Date      | 14   | 9999-99-99 99:99:99 |      |
| lessonDuration | Duration of the lesson                                 | Text      | 10   |        |      |
| lessonFocus    | Main objective of lesson                               | Text      | 18   |        |      |

Table: Member

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

Table: Membership

| Column Name        | Description                                                       | Data Type | Size | Format   | Key? |
|--------------------|-------------------------------------------------------------------|-----------|------|----------|------|
| membershipID       | Unique sequential number indicating the identification of the membership | Int       | 3    |          | PK   |
| membershipName     | Name of the membership that pertains to the member                | Text      | 10   |          |      |
| membershipPrice    | Price of the membership                                           | Text      | 3    |          |      |
| membershipDuration | Length of the membership                                          | Text      | 10   |          |      |
| membershipBenefits | Perks/benefits of having the membership                           | Text      | 25   |          |      |
| paymentID          | Unique sequential number indicating the identification of the payment of the membership | Int       | 3    |          | FK (ref. Payment) |


Table: Participant

| Column Name            | Description                                                    | Data Type | Size | Format | Key? |
|------------------------|----------------------------------------------------------------|-----------|------|--------|------|
| participationID         | Unique sequential number indicating the identification of the participant | Int       | 3    |        | PK   |
| participationDivision   | Division of tournament that participant participated in       | Text      | 20   |        |      |
| participationPlacement  | Placement of participant in the tournament                    | Text      | 15   |        |      |
| memberID               | Unique sequential number indicating the identification of the member | Int       | 3    |        | FK (ref. Member) |

Table: Payment

| Column Name    | Description                                                   | Data Type | Size | Format     | Key? |
|----------------|---------------------------------------------------------------|-----------|------|------------|------|
| paymentID      | Unique sequential number indicating the identification of the payment of the membership | Int       | 3    |            | PK   |
| paymentAmount  | Payment amount made                                           | Int       | 3    |            |      |
| paymentDate    | Date that payment was made                                    | Date      | 8    | 9999-99-99 |      |
| paymentMethod  | Method in which payment was made                              | Text      | 15   |            |      |

Table: Reservation

| Column Name         | Description                                                    | Data Type | Size | Format         | Key? |
|---------------------|----------------------------------------------------------------|-----------|------|----------------|------|
| memberID            | Unique sequential number indicating the identification of the member | Int       | 3    |                | PK, FK (ref. Member) |
| courtID             | Unique sequential number indicating the identification of the court | Int       | 3    |                | PK, FK (ref. Court)  |
| reservationDateTime | Exact date and time of reservation                            | Text      | 14   | 9999-99-99 99:99:99 |      |
| reservationDuration | Duration of reservation                                        | Text      | 10   |                |      |

Table: Results

| Column Name         | Description                                                    | Data Type | Size | Format | Key? |
|---------------------|----------------------------------------------------------------|-----------|------|--------|------|
| participant1ID      | Unique sequential number indicating the identification of the 1st participant in a game | Int       | 3    |        | PK, FK (ref. Participant) |
| tournamentID        | Unique sequential number indicating the identification of the tournament | Int       | 3    |        | PK, FK (ref. Tournament)  |
| participant2ID      | Unique sequential number indicating the identification of the 2nd participant in a game | Int       | 3    |        | PK, FK (ref. Participant) |
| participant1Score   | 1st participant’s score                                       | Text      | 3    |        |      |
| participant2Score   | 2nd participant’s score                                       | Text      | 3    |        |      |
| winner              | Winner of the game                                            | Text      | 3    |        |      |

Table: Tournament

| Column Name       | Description                                                   | Data Type | Size | Format   | Key? |
|-------------------|---------------------------------------------------------------|-----------|------|----------|------|
| tournamentID      | Unique sequential number indicating the identification of the tournament | Int       | 2    |          | PK   |
| tournamentName    | Name of tournament                                            | Text      | 20   |          |      |
| tournamentDate    | Season of tournament                                          | Text      | 10   |          |      |
| tournamentFee     | Cost to participate in tournament                             | Num       | 3    |          |      |
| tournamentPrize   | Cash prize for winning tournament                             | Num       | 4    |          |      |


## Queries
### Simple
1. Provide a list of all members who have taken lessons at the club.
```sql
SELECT DISTINCT M.memberID, M.memberFirstName, M.memberLastName
FROM Member M
JOIN Lesson L ON M.memberID = L.memberID;
```




### Complex



## Database Information
Access our database! ``al_Group_47114_G3`` on terry codrus server.

