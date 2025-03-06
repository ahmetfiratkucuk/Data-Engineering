# Data-Engineering
Database design and data processing workflows for the fitness application. Includes schema design, SQL queries, and future ETL pipelines

Fitness-Database-Examle => Data Modeling

Here a data modeling for fitness database example!!


![Fitness-Data Modeling](https://github.com/user-attachments/assets/f7ed0358-26f2-4ecc-8db6-a8c0e697c141)

This data model seems designed for a fitness or exercise tracking app. Basically, it’s a system that allows users to track their exercise, nutrition, and water consumption habits.

The data model includes:

1) A central UserInformation table. This table contains user information (name, surname, password, email, country, date of birth, height, weight, etc.).
2) The user is associated with a specific Gender, Activity Level, and Goal.
3) Users can create a Workout record. Each workout is associated with a specific exercise and body part.
4) The Exercise table shows each exercise with a difficulty level and name.
5) The ExerciseBody table is a relationship table that shows how much each exercise affects each body part.
6) Users can track their daily water consumption and nutrition goals with the WaterTracker and NutritionData tables.
7) This data model provides a comprehensive system that allows users to set fitness goals, follow their exercise programs, and track their water consumption and nutrition habits.

Fitness App Data Model

Tables and Fields

UserInformation
- User_id (int): Primary key
- User_name (nvarchar(50)): User name
- User_surname (nvarchar(50)): User surname
- User_password (nvarchar(250)): User password
- User_mail_address (nvarchar(255)): Email address
- User_country (nvarchar): Country
- User_birth_date (datetime2): Date of birth
- User_height (int): Height
- User_weight (int): Weight
- Gender_id (int): Gender - Foreign key to Gender table
- Level_id (int): Activity level - Foreign key to ActivityLevel table
- Goal_id (int): Goal - Foreign key to UserGoals table
- User_created_time (datetime2): Account creation time
- User_deleted_time (datetime2): Account deletion time

ActivityLevel
- Level_id (int): Primary key
- Level_name (nvarchar(25)): Level name

Body
- Body_id (int): Primary key
- Body_name (nvarchar(50)): Body part name

ExerciseDifficulty
- Difficulty_id (int): Primary key
- Difficulty_name (varchar(10)): Difficulty level name

Exercise
- Exercise_id (int): Primary key
- Exercise_name (nvarchar(70)): Exercise name
- Difficulty_id (int): Difficulty level - External key to ExerciseDifficulty table

ExerciseBody
- Exercise_id (int): Exercise - External key to Exercise table
- Body_id (int): Body part - External key to Body table
- Impact_level (nvarchar): Impact level

Gender
- Gender_id (int): Primary key
- Gender_name (nvarchar(25)): Gender name

UserGoals
- Goal_id (int): Primary key
- Goal_name (nvarchar(50)): Goal name

WaterTracker
- User_id (int): User - External key to UserInformation table
- User_amount_water (int): Amount of water drunk
- User_liter_goals (int): Target amount of water
- Day (datetime2): Date

NutritionData
- User_id (int): User - External key to UserInformation table
- User_liter_goals (int): Target amount of water
- User_current_weight (int): Current weight
- User_daily_calorie_goal (int): Daily calorie goal
- Day (datetime2): Date

Workout
- Workout_id (int): Primary key
- User_id (int): User - External key to UserInformation table
- Exercise_id (int): Exercise - External to Exercise table key
- Body_id (int): Body part - External key to body table
- User_set_number (nvarchar(50)): Number of sets
- User_training_time (datetime2): Workout duration

Relationships

1. UserInformation - Gender: A user has a single gender. (1:1)

2. UserInformation - ActivityLevel: A user has a single activity level. (1:1)

3. UserInformation - UserGoals: A user has a single goal. (1:1)

4. **UserInformation - WaterTracker: A user can have multiple water tracking records. (1:N)

5. UserInformation - NutritionData: A user can have multiple nutrition data. (1:N)

6. UserInformation - Workout**: A user can have multiple workout records. (1:N)

7. Exercise - ExerciseDifficulty: An exercise has a single difficulty level. (1:1)

8. Exercise - ExerciseBody: An exercise can target more than one body part. (1:N)

9. Body - ExerciseBody: A body part can be targeted in more than one exercise. (1:N)

10. Workout - Exercise: A workout consists of a single exercise. (1:1)
    
11. Workout - Body: A workout targets a single body part. (1:1)
