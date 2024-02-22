MySQL Advanced
This project contains tasks for learning advanced MySQL features.

Tasks To Complete
 0. We are all unique!
0-uniq_users.sql contains a SQL script that creates a table users following these requirements:

With these attributes:
id, integer, never null, auto increment and primary key.
email, string (255 characters), never null and unique.
name, string (255 characters).
If the table already exists, your script should not fail.
Your script can be executed on any database.
Context: Make an attribute unique directly in the table schema will enforced your business rules and avoid bugs in your application
 1. In and not out
1-country_users.sql contains a SQL script that creates a table users following these requirements:

With these attributes:
id, integer, never null, auto increment and primary key.
email, string (255 characters), never null and unique.
name, string (255 characters).
country, enumeration of countries: US, CO and TN, never null (default value will be the first element of the enumeration, which is US).
If the table already exists, your script should not fail.
Your script can be executed on any database.
 2. Best band ever!
2-fans.sql contains a SQL script that ranks country origins of bands, ordered by the number of (non-unique) fans.

Import this table dump: metal_bands.sql.
Column names must be: origin and nb_fans.
Your script can be executed on any database.
Context: Context: Calculating/computing something is always power intensive… better to distribute the load!
 3. Old school band
3-metal_bands.sql contains a SQL script that lists all bands with Glam rock as their main style, ranked by their longevity:

Import this table dump: metal_bands.sql.
Column names must be: band_name and lifespan (in years).
You should use attributes formed and split for computing the lifespan.
Your script can be executed on any database.
 4. Buy buy buy
4-store.sql contains a SQL script that creates a trigger that decreases the quantity of an item after adding a new order:

Quantity in the table items can be negative.
A dump of the database and relevant table(s) is shown below:
-- Initial
DROP TABLE IF EXISTS items;
DROP TABLE IF EXISTS orders;

CREATE TABLE IF NOT EXISTS items (
  name VARCHAR(255) NOT NULL,
  quantity int NOT NULL DEFAULT 10
);

CREATE TABLE IF NOT EXISTS orders (
  item_name VARCHAR(255) NOT NULL,
  number int NOT NULL
);

INSERT INTO items (name) VALUES ("apple"), ("pineapple"), ("pear");
Context: Updating multiple tables for one action from your application can generate issue: network disconnection, crash, etc… to keep your data in a good shape, let MySQL do it for you!
 5. Email validation to sent
5-sum_list.sql contains a SQL script that creates a trigger that resets the attribute valid_email only when the email has been changed.

A dump of the database and relevant table(s) is shown below:
-- Initial
DROP TABLE IF EXISTS users;

CREATE TABLE IF NOT EXISTS users (
  id int not null AUTO_INCREMENT,
  email varchar(255) not null,
  name varchar(255),
  valid_email boolean not null default 0,
  PRIMARY KEY (id)
);

INSERT INTO users (email, name) VALUES ("bob@dylan.com", "Bob");
INSERT INTO users (email, name, valid_email) VALUES ("sylvie@dylan.com", "Sylvie", 1);

