This tutorial won' t tackle how to install the PostgreSQL v15 on specific OS but rather just setting up the database and its schema for the backend server.

After configuring and setting up your PostgreSQL v15 database, you must execute these queries.

1. Create the database first:

   `CREATE DATABASE "PeachTreeDesigns";`

2. Connect to your database: PeachTreeDesigns

   If you're on psql, you can execute this: `\c PeachTreeDesigns;`

3. After connecting to PeachTreeDesigns database, you can now create the tables and types:

   ```
   CREATE TYPE ROLES as ENUM('ADMIN', 'REGULAR');

   DROP TABLE IF EXISTS "Post";
   DROP TABLE IF EXISTS "User";

   CREATE TABLE "User"(
       id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
       email TEXT NOT NULL,
       password TEXT NOT NULL,
       first_name TEXT NOT NULL,
       last_name TEXT NOT NULL,
       role ROLES DEFAULT 'ADMIN',
       created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
       updated_at TIMESTAMP,
       UNIQUE(id),
       UNIQUE(email)
   );

   CREATE TABLE "Post"(
       id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
       created_at TIMESTAMP NOT NULL,
       updated_at TIMESTAMP,
       content_title TEXT NOT NULL,
       content_text TEXT NOT NULL,
       content_photos TEXT[],
       category TEXT,
       user_id UUID NOT NULL,
       CONSTRAINT fk_user_id FOREIGN KEY (user_id) REFERENCES "User"(id),
       UNIQUE(id)
   );

   -- CREATE ADMIN USER
   -- PASSWORD MUST BE HASHED BY ARGON2 IF NOT, IT'LL NOT WORK
   INSERT INTO "User"(email, password, first_name, last_name)
   VALUES ('ptd@ptd.com', '$argon2id$v=19$m=65536,t=3,p=4$M2+/gjOcZERViyvwuVSkuQ$0ShSuGJjoNGNQ55YOGeA1/i5Ve1cJguTtBBgiYlJ5dY', 'Peach Tree', 'Designs');
   -- Default credentials:
   -- Email: ptd@ptd.com (change to your email)
   -- Pass: peachtreedesigns
   ```

   Done! You may proceed to setting up your backend server. 🚀🥳🎉
