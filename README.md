# Carvago SQL practical part

## Prerequisites
1. Download `docker-compose` [at this link](https://docs.docker.com/compose/install/)
   2. You can either install the docker desktop which comes with `docker-compose`, or if you have the docker engine and/or docker CLI, you just need to install the compose plugin from command line.
2. Download _any_ preferred GUI tool for database management. In the presentation, we'll use [Tableplus](https://tableplus.com/)


## How to run
1. In repo directory, open command line and write `docker-compose up`
2. DB should be up and running. You can connect to it with the credentials specified in `docker-compose.yml`

# DB diagram
![DB to create](/img/db.png)
Our job will be to create this DB structure.

Note: the relation between `vehicles` and `users` is `m:n`, but the junction table `vehicles_users` is not shown in the diagram :).

### After successful DB creation, use these following inserts to insert some data.
```sql
-- Insert 10 rows into the users table
INSERT INTO users (username, is_admin, created_at)
VALUES 
  ('user1', false, NOW()),
  ('user2', false, NOW()),
  ('user3', false, NOW()),
  ('user4', false, NOW()),
  ('user5', false, NOW()),
  ('user6', false, NOW()),
  ('user7', false, NOW()),
  ('user8', false, NOW()),
  ('user9', true, NOW()),
  ('user10', true, NOW());
```

```sql
-- Insert 50 rows into the posts table
INSERT INTO posts (title, body, user_id, status, created_at)
SELECT 
  CONCAT('Post Title ', ROW_NUMBER() OVER()), 
  'This is a sample post body.',
  FLOOR(1 + (RANDOM() * 10)),  -- Randomly select user_id between 1 and 10
  'published',
  NOW()
FROM 
  generate_series(1, 50);  -- Generate 50 rows
```

```sql
-- Insert 20 rows into the vehicles table
INSERT INTO vehicles (make, type)
VALUES 
  ('Toyota', 'Sedan'),
  ('Honda', 'SUV'),
  ('Ford', 'Truck'),
  ('Chevrolet', 'Coupe'),
  ('Nissan', 'Hatchback'),
  ('Hyundai', 'Convertible'),
  ('Kia', 'Minivan'),
  ('BMW', 'Wagon'),
  ('Mercedes', 'Sportscar'),
  ('Audi', 'Luxury'),
  ('Volkswagen', 'Crossover'),
  ('Subaru', 'Roadster'),
  ('Jeep', 'Pickup'),
  ('Lexus', 'SUV'),
  ('Mazda', 'Sedan'),
  ('Porsche', 'Coupe'),
  ('Jaguar', 'Convertible'),
  ('Land Rover', 'SUV'),
  ('Infiniti', 'Luxury'),
  ('Buick', 'Sedan'),
  ('Chrysler', 'Van');
```

```sql
-- Insert sample rows into the vehicles_users table
INSERT INTO vehicles_users (vehicle_id, user_id)
VALUES
  (3, 5),
  (4, 5),
  (7, 5),
  (15, 5),
  (1, 2),
  (2, 2),
  (3, 2),
  (1, 4),
  (20, 4),
  (21, 4), 
  (1, 6), 
  (1, 7), 
  (1, 8), 
  (1, 9), 
  (1, 10), 
  (2, 10), 
  (3, 10), 
  (4, 10), 
  (5, 10), 
  (6, 10);
```

## Additional tasks
1. Select everything from all users.
2. List all admin user
3. Find all posts created by a specific user - `user5`
4. Count number of posts per user
5. Select All vehicles and their owners
6. Find users without posts
7. List posts with status and username
8. Find all vehicles of admin users
9. Select users and the date they created their first post
10. Find users who have both posts and vehicles in DB
