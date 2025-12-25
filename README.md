# Лабораторная работа №1
![](zxc.png)
# Лабораторная работа №2
###

``` sql
CREATE TABLE "Emelyanov2271"."Player" (
    player_id INT PRIMARY KEY NOT NULL,
  name VARCHAR(50) NOT NULL,
  nickname VARCHAR(50) NOT NULL,
  email VARCHAR(255) NOT NULL UNIQUE,
  registered_date DATE
);

CREATE TABLE "Emelyanov2271"."Session"(
  session_id INT PRIMARY KEY NOT NULL,
  name VARCHAR(50) NOT NULL,
  region VARCHAR(50),
  difficulty INT NOT NULL DEFAULT 1
);

CREATE TABLE "Emelyanov2271"."Stat_catalog"(
  stat_id INT PRIMARY KEY NOT NULL,
  name_stat VARCHAR(50) NOT NULL
);

CREATE TABLE "Emelyanov2271"."Class_catalog"(
  class_id INT PRIMARY KEY NOT NULL,
  name_class VARCHAR(50) NOT NULL
);

CREATE TABLE "Emelyanov2271"."Character"(
  character_id INT PRIMARY KEY NOT NULL,
  name VARCHAR(50) NOT NULL DEFAULT 'Hero',
  class_id INT NOT NULL DEFAULT 0,
  level INT NOT NULL,
  experience INT NOT NULL,
  session_id INT NOT NULL  DEFAULT 0,
  player_id INT NOT NULL,
  create_date DATE
);

CREATE TABLE "Emelyanov2271"."Character_stat"(
  character_id INT NOT NULL,
    stat_id INT NOT NULL,
  PRIMARY KEY(character_id,stat_id),
  value INT NOT NULL
);
```
``` sql
INSERT INTO "Emelyanov2271"."Player"
(player_id, "name", nickname, email, registered_date) 
VALUES (0, 'kosty', 'kosty', 'kosty@yandex.ru', '21.09.25');

INSERT INTO "Emelyanov2271"."Player"
(player_id, "name", nickname, email, registered_date) 
VALUES (1, 'Vika', 'Akiv', 'Akiv@yandex.ru', '21.09.25');

INSERT INTO "Emelyanov2271"."Player"
(player_id, "name", nickname, email, registered_date) 
VALUES (2, 'Vadim', 'Midav', 'Midav@gmail.com', '21.09.25'),
(3, 'Nikita', 'Atikin', 'Atikin@gmail.com', '27.09.25');

INSERT INTO "Emelyanov2271"."Session"
(session_id, "name", region, difficulty) 
VALUES (0, 'Patygame', 'Russia', 2),
(1, 'kostygame', 'Russia', 1),
(2, 'Akivgame', 'Japan', 0),
(3, 'Midavgame', 'Europ', 1);

INSERT INTO "Emelyanov2271"."Stat_catalog"
(stat_id, name_stat) 
VALUES (0, 'Strength'),
(1, 'Agility'),
(2, 'Intelligence'),
(3, 'Endurance');

INSERT INTO "Emelyanov2271"."Class_catalog"
(class_id, name_class) 
VALUES (0, 'Warrior'),
(1, 'Archer'),
(2, 'Wizard'),
(3, 'Assassin');

INSERT INTO "Emelyanov2271"."Character"
(character_id, "name", class_id, "level", "experience", session_id, player_id, create_date) 
VALUES (0, 'Char1', 2, 6, 280, 0, 0, '22.09.25');

INSERT INTO "Emelyanov2271"."Character"
(character_id, "name", class_id, "level", "experience", session_id, player_id, create_date) 
VALUES (1, 'Char2', 1, 5, 970, 0, 2, '22.09.25'),
(2, 'Char3', 0, 5, 890, 2, 1, '25.09.25'),
(3, 'Char4', 3, 7, 100, 0, 3, '22.09.25');

INSERT INTO "Emelyanov2271"."Character"
(character_id, "name", class_id, "level", "experience", session_id, player_id, create_date) 
VALUES (4, 'Char5', 0, 6, 990, 0, 0, '22.09.25');

INSERT INTO "Emelyanov2271"."Character_stat"
(character_id, stat_id, "value") 
VALUES  (0, 0, 10),
	(0, 1, 14),
	(0, 2, 20),
	(0, 3, 8);
INSERT INTO "Emelyanov2271"."Character_stat"
(character_id, stat_id, "value") 
VALUES  (1, 0, 10),
	(1, 1, 18),
	(1, 2, 10),
	(1, 3, 14);
INSERT INTO "Emelyanov2271"."Character_stat"
(character_id, stat_id, "value") 
VALUES  (2, 0, 18),
	(2, 1, 12),
	(2, 2, 8),
	(2, 3, 16);
```
``` sql
SELECT 
  "Emelyanov2271"."Player".nickname,
  "Emelyanov2271"."Character".name,
  "Emelyanov2271"."Class_catalog".name_class,
  "Emelyanov2271"."Character".level,
  "Emelyanov2271"."Stat_catalog".name_stat,
  "Emelyanov2271"."Character_stat".value
FROM "Emelyanov2271"."Player"
INNER JOIN "Emelyanov2271"."Character"
  ON "Emelyanov2271"."Player".player_id = "Emelyanov2271"."Character".player_id
INNER JOIN "Emelyanov2271"."Character_stat"
  On "Emelyanov2271"."Character".character_id = "Emelyanov2271"."Character_stat".character_id
INNER JOIN "Emelyanov2271"."Stat_catalog"
  On "Emelyanov2271"."Stat_catalog".stat_id = "Emelyanov2271"."Character_stat".stat_id
INNER JOIN "Emelyanov2271"."Class_catalog"
  On "Emelyanov2271"."Character".class_id = "Emelyanov2271"."Class_catalog".class_id;
```
 
