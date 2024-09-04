# Carvago SQL practical part

## Prerequisities
1. Download `docker-compose` [at this link](https://docs.docker.com/compose/install/)
   2. You can either install the docker desktop which comes with `docker-compose`, or if you have the docker engine and/or docker CLI, you just need to install the compose plugin from command line.
2. Download _any_ preferred GUI tool for database management. We'll use [Tableplus](https://tableplus.com/)


# DB diagram
![DB to create](/img/db.png)
Our job will be to create this DB structure.

Note: the relation between `vehicles` and `users` is `m:n`, but the junction table is not shown in the diagram.

After successful DB creation, use these following inserts to insert some data.
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
INSERT INTO vehicles_users (vehicles_id, users_id)
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
1. a
2. a
3. a
4. a
5. a
6. a
7. a
8. a
