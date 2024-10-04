# Social-media-database-case-study-
THE CODES AND THE DATABASES GIVEN BELOW ARE USED IN THE CASE STUDY....

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| hospital           |
| information_schema |
| instagram          |
| karthi             |
| mid1               |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
8 rows in set (0.01 sec)

mysql> use instagram;
Database changed
mysql> show tables;
Empty set (0.00 sec)

mysql> CREATE TABLE Account (
    ->     user_id INT PRIMARY KEY,
    ->     user_name VARCHAR(50),
    ->     type VARCHAR(50),
    ->     DOB DATE
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> CREATE TABLE backend (
    ->     user_id INT,
    ->     phone_number VARCHAR(50),
    ->     email_id VARCHAR(50),
    ->     education VARCHAR(50),
    ->     location VARCHAR(50),
    ->     relationship VARCHAR(50),
    ->     i_password VARCHAR(50),
    ->     f_password VARCHAR(50),
    ->     login_device VARCHAR(50),
    ->     FOREIGN KEY (user_id) REFERENCES Account(user_id)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> CREATE TABLE details (
    ->     user_id INT,
    ->     user_name VARCHAR(50),
    ->     no_of_photos INT,
    ->     no_of_friends INT,
    ->     no_of_reels INT,
    ->     no_of_posts INT,
    ->     following INT,
    ->     followers INT,
    ->     status VARCHAR(50),
    ->     FOREIGN KEY (user_id) REFERENCES Account(user_id)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> CREATE TABLE insta (
    ->     user_id INT,
    ->     post_id INT PRIMARY KEY,
    ->     likes INT,
    ->     shares INT,
    ->     comments INT,
    ->     FOREIGN KEY (user_id) REFERENCES Account(user_id)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> CREATE TABLE facebook (
    ->     user_id INT,
    ->     photo_id INT PRIMARY KEY,
    ->     likes INT,
    ->     shares INT,
    ->     comments INT,
    ->     FOREIGN KEY (user_id) REFERENCES Account(user_id)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> INSERT INTO Account (user_id, user_name, type, DOB)
    -> VALUES
    ->     (244, 'Nallam Nikhil Reddy', 'instagram', '2004-08-16'),
    ->     (285, 'Galla Karthikeya', 'instagram', '2004-06-07'),
    ->     (303, 'Putta Ganesh Kumar', 'instagram', '2004-03-22'),
    ->     (389, 'Gopireddy Manoj Reddy', 'instagram', '2004-08-28'),
    ->     (244, 'Nallam Nikhil Reddy', 'facebook', '2004-08-16'),
    ->     (285, 'Galla Karthikeya', 'facebook', '2004-06-07'),
    ->     (303, 'Putta Ganesh Kumar', 'facebook', '2004-03-22'),
    ->     (389, 'Gopireddy Manoj Reddy', 'facebook', '2004-08-28');
ERROR 1062 (23000): Duplicate entry '244' for key 'account.PRIMARY'
mysql> INSERT INTO Account (user_id, user_name, type, DOB)
    -> VALUES
    ->     (2441, 'Nallam Nikhil Reddy', 'instagram', '2004-08-16'),
    ->     (2851, 'Galla Karthikeya', 'instagram', '2004-06-07'),
    ->     (3031, 'Putta Ganesh Kumar', 'instagram', '2004-03-22'),
    ->     (3891, 'Gopireddy Manoj Reddy', 'instagram', '2004-08-28'),
    ->     (2442, 'Nallam Nikhil Reddy', 'facebook', '2004-08-16'),
    ->     (2852, 'Galla Karthikeya', 'facebook', '2004-06-07'),
    ->     (3032, 'Putta Ganesh Kumar', 'facebook', '2004-03-22'),
    ->     (3892, 'Gopireddy Manoj Reddy', 'facebook', '2004-08-28');
Query OK, 8 rows affected (0.03 sec)
Records: 8  Duplicates: 0  Warnings: 0

mysql> select * from Account;
+---------+-----------------------+-----------+------------+
| user_id | user_name             | type      | DOB        |
+---------+-----------------------+-----------+------------+
|    2441 | Nallam Nikhil Reddy   | instagram | 2004-08-16 |
|    2442 | Nallam Nikhil Reddy   | facebook  | 2004-08-16 |
|    2851 | Galla Karthikeya      | instagram | 2004-06-07 |
|    2852 | Galla Karthikeya      | facebook  | 2004-06-07 |
|    3031 | Putta Ganesh Kumar    | instagram | 2004-03-22 |
|    3032 | Putta Ganesh Kumar    | facebook  | 2004-03-22 |
|    3891 | Gopireddy Manoj Reddy | instagram | 2004-08-28 |
|    3892 | Gopireddy Manoj Reddy | facebook  | 2004-08-28 |
+---------+-----------------------+-----------+------------+
8 rows in set (0.00 sec)

mysql> INSERT INTO backend (user_id, phone_number, email_id, education, location, relationship, i_password, f_password, login_device)
    -> VALUES
    ->     (2441, '8309531322', 'nnallam@gitam.in', 'PHD', 'Chittor', '3 girl friends', 'loverboy_244', 'loverboy_244', 'vivo y50'),
    ->     (2851, '6305302998', 'kgalla@gitam.in', 'MBA', 'Nellore', 'single', 'Karthikeya@123', 'Karthikeya@123', 'oppo reno 8'),
    ->     (3031, '6304843780', 'gputta@gitam.in', 'MTech', 'Guntur', '2 girl friends', 'ganesh@123', 'ganesh@123', 'oneplus 10 pro'),
    ->     (3891, '9390973191', 'mgopired@gitam.in', 'B.Tech', 'Kadapa', 'mingle', 'manoj@456', 'manoj@456', 'realme z pro'),
    ->     (2442, '8309531322', 'nnallam@gitam.in', 'PHD', 'Chittor', '3 girl friends', 'loverboy_244', 'loverboy_244', 'vivo y50'),
    ->     (2852, '6305302998', 'kgalla@gitam.in', 'MBA', 'Nellore', 'single', 'Karthikeya@123', 'Karthikeya@123', 'oppo reno 8'),
    ->     (3032, '6304843780', 'gputta@gitam.in', 'MTech', 'Guntur', '2 girl friends', 'ganesh@123', 'ganesh@123', 'oneplus 10 pro'),
    ->     (3892, '9390973191', 'mgopired@gitam.in', 'B.Tech', 'Kadapa', 'mingle', 'manoj@456', 'manoj@456', 'realme z pro');
Query OK, 8 rows affected (0.01 sec)
Records: 8  Duplicates: 0  Warnings: 0

mysql> select * from backend;
+---------+--------------+-------------------+-----------+----------+----------------+----------------+----------------+----------------+
| user_id | phone_number | email_id          | education | location | relationship   | i_password     | f_password     | login_device   |
+---------+--------------+-------------------+-----------+----------+----------------+----------------+----------------+----------------+
|    2441 | 8309531322   | nnallam@gitam.in  | PHD       | Chittor  | 3 girl friends | loverboy_244   | loverboy_244   | vivo y50       |
|    2851 | 6305302998   | kgalla@gitam.in   | MBA       | Nellore  | single         | Karthikeya@123 | Karthikeya@123 | oppo reno 8    |
|    3031 | 6304843780   | gputta@gitam.in   | MTech     | Guntur   | 2 girl friends | ganesh@123     | ganesh@123     | oneplus 10 pro |
|    3891 | 9390973191   | mgopired@gitam.in | B.Tech    | Kadapa   | mingle         | manoj@456      | manoj@456      | realme z pro   |
|    2442 | 8309531322   | nnallam@gitam.in  | PHD       | Chittor  | 3 girl friends | loverboy_244   | loverboy_244   | vivo y50       |
|    2852 | 6305302998   | kgalla@gitam.in   | MBA       | Nellore  | single         | Karthikeya@123 | Karthikeya@123 | oppo reno 8    |
|    3032 | 6304843780   | gputta@gitam.in   | MTech     | Guntur   | 2 girl friends | ganesh@123     | ganesh@123     | oneplus 10 pro |
|    3892 | 9390973191   | mgopired@gitam.in | B.Tech    | Kadapa   | mingle         | manoj@456      | manoj@456      | realme z pro   |
+---------+--------------+-------------------+-----------+----------+----------------+----------------+----------------+----------------+
8 rows in set (0.00 sec)

mysql> INSERT INTO details (user_id, user_name, no_of_photos, no_of_friends, no_of_reels, no_of_posts, following, followers, status)
    -> VALUES
    ->     (2441, 'Nallam Nikhil Reddy', 75, 450, 30, 150, 300, 750, 'public'),
    ->     (2851, 'Galla Karthikeya', 60, 380, 25, 120, 250, 650, 'private'),
    ->     (3031, 'Putta Ganesh Kumar', 80, 520, 35, 180, 350, 800, 'public'),
    ->     (3891, 'Gopireddy Manoj Reddy', 70, 420, 28, 140, 320, 720, 'private'),
    ->     (2442, 'Nallam Nikhil Reddy', 75, 450, 30, 150, 300, 750, 'public'),
    ->     (2852, 'Galla Karthikeya', 60, 380, 25, 120, 250, 650, 'private'),
    ->     (3032, 'Putta Ganesh Kumar', 80, 520, 35, 180, 350, 800, 'public'),
    ->     (3892, 'Gopireddy Manoj Reddy', 70, 420, 28, 140, 320, 720, 'private');
Query OK, 8 rows affected (0.01 sec)
Records: 8  Duplicates: 0  Warnings: 0

mysql> select * from details;
+---------+-----------------------+--------------+---------------+-------------+-------------+-----------+-----------+---------+
| user_id | user_name             | no_of_photos | no_of_friends | no_of_reels | no_of_posts | following | followers | status  |
+---------+-----------------------+--------------+---------------+-------------+-------------+-----------+-----------+---------+
|    2441 | Nallam Nikhil Reddy   |           75 |           450 |          30 |         150 |       300 |       750 | public  |
|    2851 | Galla Karthikeya      |           60 |           380 |          25 |         120 |       250 |       650 | private |
|    3031 | Putta Ganesh Kumar    |           80 |           520 |          35 |         180 |       350 |       800 | public  |
|    3891 | Gopireddy Manoj Reddy |           70 |           420 |          28 |         140 |       320 |       720 | private |
|    2442 | Nallam Nikhil Reddy   |           75 |           450 |          30 |         150 |       300 |       750 | public  |
|    2852 | Galla Karthikeya      |           60 |           380 |          25 |         120 |       250 |       650 | private |
|    3032 | Putta Ganesh Kumar    |           80 |           520 |          35 |         180 |       350 |       800 | public  |
|    3892 | Gopireddy Manoj Reddy |           70 |           420 |          28 |         140 |       320 |       720 | private |
+---------+-----------------------+--------------+---------------+-------------+-------------+-----------+-----------+---------+
8 rows in set (0.00 sec)

mysql> INSERT INTO insta (user_id, post_id, likes, shares, comments)
    -> VALUES
    ->     (2441, '244001', 180, 50, 120),
    ->     (2441, '244002', 140, 25, 150),
    ->     (2441, '244003', 120, 45, 125),
    ->     (2441, '244004', 190, 21, 103),
    ->     (2441, '244005', 140, 55, 127),
    ->     (2441, '244006', 110, 24, 141),
    ->     (2441, '244007', 160, 34, 134),
    ->     (2441, '244008', 210, 78, 123),
    ->     (2441, '244009', 250, 80, 147),
    ->     (2441, '244010', 270, 89, 180);
Query OK, 10 rows affected (0.03 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO insta (user_id, post_id, likes, shares, comments)
    -> VALUES
    ->     (2851, '285001', 180, 50, 120),
    ->     (2851, '285002', 160, 45, 130),
    ->     (2851, '285003', 140, 40, 110),
    ->     (2851, '285004', 200, 60, 150),
    ->     (2851, '285005', 190, 55, 140),
    ->     (2851, '285006', 170, 48, 135),
    ->     (2851, '285007', 210, 62, 155),
    ->     (2851, '285008', 220, 65, 165),
    ->     (2851, '285009', 230, 68, 175),
    ->     (2851, '285010', 240, 70, 185);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO insta (user_id, post_id, likes, shares, comments)
    -> VALUES
    ->     (3031, '303001', 220, 60, 130),
    ->     (3031, '303002', 210, 55, 125),
    ->     (3031, '303003', 240, 70, 140),
    ->     (3031, '303004', 250, 75, 150),
    ->     (3031, '303005', 230, 68, 145),
    ->     (3031, '303006', 260, 80, 160),
    ->     (3031, '303007', 270, 85, 170),
    ->     (3031, '303008', 280, 88, 180),
    ->     (3031, '303009', 290, 90, 190),
    ->     (3031, '303010', 300, 95, 200);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO insta (user_id, post_id, likes, shares, comments)
    -> VALUES
    ->     (3891, '389001', 160, 45, 110),
    ->     (3891, '389002', 140, 40, 100),
    ->     (3891, '389003', 180, 50, 120),
    ->     (3891, '389004', 200, 55, 130),
    ->     (3891, '389005', 190, 52, 125),
    ->     (3891, '389006', 170, 48, 115),
    ->     (3891, '389007', 210, 60, 135),
    ->     (3891, '389008', 220, 65, 145),
    ->     (3891, '389009', 230, 68, 155),
    ->     (3891, '389010', 240, 70, 165);
Query OK, 10 rows affected (0.00 sec)
Records: 10  Duplicates: 0  Warnings: 0


mysql> select * from insta;
+---------+---------+-------+--------+----------+
| user_id | post_id | likes | shares | comments |
+---------+---------+-------+--------+----------+
|    2441 |  244001 |   180 |     50 |      120 |
|    2441 |  244002 |   140 |     25 |      150 |
|    2441 |  244003 |   120 |     45 |      125 |
|    2441 |  244004 |   190 |     21 |      103 |
|    2441 |  244005 |   140 |     55 |      127 |
|    2441 |  244006 |   110 |     24 |      141 |
|    2441 |  244007 |   160 |     34 |      134 |
|    2441 |  244008 |   210 |     78 |      123 |
|    2441 |  244009 |   250 |     80 |      147 |
|    2441 |  244010 |   270 |     89 |      180 |
|    2851 |  285001 |   180 |     50 |      120 |
|    2851 |  285002 |   160 |     45 |      130 |
|    2851 |  285003 |   140 |     40 |      110 |
|    2851 |  285004 |   200 |     60 |      150 |
|    2851 |  285005 |   190 |     55 |      140 |
|    2851 |  285006 |   170 |     48 |      135 |
|    2851 |  285007 |   210 |     62 |      155 |
|    2851 |  285008 |   220 |     65 |      165 |
|    2851 |  285009 |   230 |     68 |      175 |
|    2851 |  285010 |   240 |     70 |      185 |
|    3031 |  303001 |   220 |     60 |      130 |
|    3031 |  303002 |   210 |     55 |      125 |
|    3031 |  303003 |   240 |     70 |      140 |
|    3031 |  303004 |   250 |     75 |      150 |
|    3031 |  303005 |   230 |     68 |      145 |
|    3031 |  303006 |   260 |     80 |      160 |
|    3031 |  303007 |   270 |     85 |      170 |
|    3031 |  303008 |   280 |     88 |      180 |
|    3031 |  303009 |   290 |     90 |      190 |
|    3031 |  303010 |   300 |     95 |      200 |
|    3891 |  389001 |   160 |     45 |      110 |
|    3891 |  389002 |   140 |     40 |      100 |
|    3891 |  389003 |   180 |     50 |      120 |
|    3891 |  389004 |   200 |     55 |      130 |
|    3891 |  389005 |   190 |     52 |      125 |
|    3891 |  389006 |   170 |     48 |      115 |
|    3891 |  389007 |   210 |     60 |      135 |
|    3891 |  389008 |   220 |     65 |      145 |
|    3891 |  389009 |   230 |     68 |      155 |
|    3891 |  389010 |   240 |     70 |      165 |
+---------+---------+-------+--------+----------+
40 rows in set (0.00 sec)

mysql> select * from insta where user_id = 2441;
+---------+---------+-------+--------+----------+
| user_id | post_id | likes | shares | comments |
+---------+---------+-------+--------+----------+
|    2441 |  244001 |   180 |     50 |      120 |
|    2441 |  244002 |   140 |     25 |      150 |
|    2441 |  244003 |   120 |     45 |      125 |
|    2441 |  244004 |   190 |     21 |      103 |
|    2441 |  244005 |   140 |     55 |      127 |
|    2441 |  244006 |   110 |     24 |      141 |
|    2441 |  244007 |   160 |     34 |      134 |
|    2441 |  244008 |   210 |     78 |      123 |
|    2441 |  244009 |   250 |     80 |      147 |
|    2441 |  244010 |   270 |     89 |      180 |
+---------+---------+-------+--------+----------+
10 rows in set (0.00 sec)

mysql> INSERT INTO facebook (user_id, photo_id, likes, shares, comments)
    -> VALUES
    ->     (2442, 1001, 180, 50, 120),
    ->     (2442, 1002, 140, 25, 150),
    ->     (2442, 1003, 120, 45, 125),
    ->     (2442, 1004, 190, 21, 103),
    ->     (2442, 1005, 140, 55, 127),
    ->     (2442, 1006, 110, 24, 141),
    ->     (2442, 1007, 160, 34, 134),
    ->     (2442, 1008, 210, 78, 123),
    ->     (2442, 1009, 250, 80, 147),
    ->     (2442, 1010, 270, 89, 180);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO facebook (user_id, photo_id, likes, shares, comments)
    -> VALUES
    ->     (2852, 2001, 220, 60, 130),
    ->     (2852, 2002, 210, 55, 125),
    ->     (2852, 2003, 240, 70, 140),
    ->     (2852, 2004, 250, 75, 150),
    ->     (2852, 2005, 230, 68, 145),
    ->     (2852, 2006, 260, 80, 160),
    ->     (2852, 2007, 270, 85, 170),
    ->     (2852, 2008, 280, 88, 180),
    ->     (2852, 2009, 290, 90, 190),
    ->     (2852, 2010, 300, 95, 200);
Query OK, 10 rows affected (0.00 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO facebook (user_id, photo_id, likes, shares, comments)
    -> VALUES
    ->     (3032, 3001, 160, 45, 110),
    ->     (3032, 3002, 140, 40, 100),
    ->     (3032, 3003, 180, 50, 120),
    ->     (3032, 3004, 200, 55, 130),
    ->     (3032, 3005, 190, 52, 125),
    ->     (3032, 3006, 170, 48, 115),
    ->     (3032, 3007, 210, 60, 135),
    ->     (3032, 3008, 220, 65, 145),
    ->     (3032, 3009, 230, 68, 155),
    ->     (3032, 3010, 240, 70, 165);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> INSERT INTO facebook (user_id, photo_id, likes, shares, comments)
    -> VALUES
    ->     (3892, 4001, 170, 55, 120),
    ->     (3892, 4002, 150, 50, 110),
    ->     (3892, 4003, 190, 60, 130),
    ->     (3892, 4004, 210, 65, 140),
    ->     (3892, 4005, 200, 62, 135),
    ->     (3892, 4006, 180, 58, 125),
    ->     (3892, 4007, 220, 70, 145),
    ->     (3892, 4008, 230, 72, 155),
    ->     (3892, 4009, 240, 75, 165),
    ->     (3892, 4010, 250, 80, 175);
Query OK, 10 rows affected (0.01 sec)
Records: 10  Duplicates: 0  Warnings: 0

mysql> select * from facebook;
+---------+----------+-------+--------+----------+
| user_id | photo_id | likes | shares | comments |
+---------+----------+-------+--------+----------+
|    2442 |     1001 |   180 |     50 |      120 |
|    2442 |     1002 |   140 |     25 |      150 |
|    2442 |     1003 |   120 |     45 |      125 |
|    2442 |     1004 |   190 |     21 |      103 |
|    2442 |     1005 |   140 |     55 |      127 |
|    2442 |     1006 |   110 |     24 |      141 |
|    2442 |     1007 |   160 |     34 |      134 |
|    2442 |     1008 |   210 |     78 |      123 |
|    2442 |     1009 |   250 |     80 |      147 |
|    2442 |     1010 |   270 |     89 |      180 |
|    2852 |     2001 |   220 |     60 |      130 |
|    2852 |     2002 |   210 |     55 |      125 |
|    2852 |     2003 |   240 |     70 |      140 |
|    2852 |     2004 |   250 |     75 |      150 |
|    2852 |     2005 |   230 |     68 |      145 |
|    2852 |     2006 |   260 |     80 |      160 |
|    2852 |     2007 |   270 |     85 |      170 |
|    2852 |     2008 |   280 |     88 |      180 |
|    2852 |     2009 |   290 |     90 |      190 |
|    2852 |     2010 |   300 |     95 |      200 |
|    3032 |     3001 |   160 |     45 |      110 |
|    3032 |     3002 |   140 |     40 |      100 |
|    3032 |     3003 |   180 |     50 |      120 |
|    3032 |     3004 |   200 |     55 |      130 |
|    3032 |     3005 |   190 |     52 |      125 |
|    3032 |     3006 |   170 |     48 |      115 |
|    3032 |     3007 |   210 |     60 |      135 |
|    3032 |     3008 |   220 |     65 |      145 |
|    3032 |     3009 |   230 |     68 |      155 |
|    3032 |     3010 |   240 |     70 |      165 |
|    3892 |     4001 |   170 |     55 |      120 |
|    3892 |     4002 |   150 |     50 |      110 |
|    3892 |     4003 |   190 |     60 |      130 |
|    3892 |     4004 |   210 |     65 |      140 |
|    3892 |     4005 |   200 |     62 |      135 |
|    3892 |     4006 |   180 |     58 |      125 |
|    3892 |     4007 |   220 |     70 |      145 |
|    3892 |     4008 |   230 |     72 |      155 |
|    3892 |     4009 |   240 |     75 |      165 |
|    3892 |     4010 |   250 |     80 |      175 |
+---------+----------+-------+--------+----------+
40 rows in set (0.00 sec)

mysql> select * from facebook where user_id = 2852;
+---------+----------+-------+--------+----------+
| user_id | photo_id | likes | shares | comments |
+---------+----------+-------+--------+----------+
|    2852 |     2001 |   220 |     60 |      130 |
|    2852 |     2002 |   210 |     55 |      125 |
|    2852 |     2003 |   240 |     70 |      140 |
|    2852 |     2004 |   250 |     75 |      150 |
|    2852 |     2005 |   230 |     68 |      145 |
|    2852 |     2006 |   260 |     80 |      160 |
|    2852 |     2007 |   270 |     85 |      170 |
|    2852 |     2008 |   280 |     88 |      180 |
|    2852 |     2009 |   290 |     90 |      190 |
|    2852 |     2010 |   300 |     95 |      200 |
+---------+----------+-------+--------+----------+
10 rows in set (0.00 sec)


mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM Account AS a
    -> JOIN facebook AS f ON a.user_id = f.user_id
    -> WHERE a.user_id = 2851;
Empty set (0.01 sec)

mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM Account AS a
    -> JOIN facebook AS f ON a.user_id = f.user_id
    -> WHERE a.user_id = 2852;
+---------+------------------+----------+-------+--------+----------+
| user_id | user_name        | photo_id | likes | shares | comments |
+---------+------------------+----------+-------+--------+----------+
|    2852 | Galla Karthikeya |     2001 |   220 |     60 |      130 |
|    2852 | Galla Karthikeya |     2002 |   210 |     55 |      125 |
|    2852 | Galla Karthikeya |     2003 |   240 |     70 |      140 |
|    2852 | Galla Karthikeya |     2004 |   250 |     75 |      150 |
|    2852 | Galla Karthikeya |     2005 |   230 |     68 |      145 |
|    2852 | Galla Karthikeya |     2006 |   260 |     80 |      160 |
|    2852 | Galla Karthikeya |     2007 |   270 |     85 |      170 |
|    2852 | Galla Karthikeya |     2008 |   280 |     88 |      180 |
|    2852 | Galla Karthikeya |     2009 |   290 |     90 |      190 |
|    2852 | Galla Karthikeya |     2010 |   300 |     95 |      200 |
+---------+------------------+----------+-------+--------+----------+
10 rows in set (0.00 sec)

mysql> select a.user_id, a.user_name, i.post_id, i.likes, i.shares, i.comments
    -> from insta as i
    -> join Account as a on a.user_id = i.user_id
    -> where a.user_id = 2441;
+---------+---------------------+---------+-------+--------+----------+
| user_id | user_name           | post_id | likes | shares | comments |
+---------+---------------------+---------+-------+--------+----------+
|    2441 | Nallam Nikhil Reddy |  244001 |   180 |     50 |      120 |
|    2441 | Nallam Nikhil Reddy |  244002 |   140 |     25 |      150 |
|    2441 | Nallam Nikhil Reddy |  244003 |   120 |     45 |      125 |
|    2441 | Nallam Nikhil Reddy |  244004 |   190 |     21 |      103 |
|    2441 | Nallam Nikhil Reddy |  244005 |   140 |     55 |      127 |
|    2441 | Nallam Nikhil Reddy |  244006 |   110 |     24 |      141 |
|    2441 | Nallam Nikhil Reddy |  244007 |   160 |     34 |      134 |
|    2441 | Nallam Nikhil Reddy |  244008 |   210 |     78 |      123 |
|    2441 | Nallam Nikhil Reddy |  244009 |   250 |     80 |      147 |
|    2441 | Nallam Nikhil Reddy |  244010 |   270 |     89 |      180 |
+---------+---------------------+---------+-------+--------+----------+
10 rows in set (0.00 sec)


mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM (
    ->     SELECT user_id, user_name
    ->     FROM Account
    ->     WHERE user_id = 2851
    -> ) AS a
    -> JOIN (
    ->     SELECT user_id, photo_id, likes, shares, comments
    ->     FROM facebook
    -> ) AS f ON a.user_id = f.user_id;
Empty set (0.00 sec)

mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM (
    ->     SELECT user_id, user_name
    ->     FROM Account
    ->     WHERE user_id = 2852
    -> ) AS a
    -> JOIN (
    ->     SELECT user_id, photo_id, likes, shares, comments
    ->     FROM facebook
    -> ) AS f ON a.user_id = f.user_id;
+---------+------------------+----------+-------+--------+----------+
| user_id | user_name        | photo_id | likes | shares | comments |
+---------+------------------+----------+-------+--------+----------+
|    2852 | Galla Karthikeya |     2001 |   220 |     60 |      130 |
|    2852 | Galla Karthikeya |     2002 |   210 |     55 |      125 |
|    2852 | Galla Karthikeya |     2003 |   240 |     70 |      140 |
|    2852 | Galla Karthikeya |     2004 |   250 |     75 |      150 |
|    2852 | Galla Karthikeya |     2005 |   230 |     68 |      145 |
|    2852 | Galla Karthikeya |     2006 |   260 |     80 |      160 |
|    2852 | Galla Karthikeya |     2007 |   270 |     85 |      170 |
|    2852 | Galla Karthikeya |     2008 |   280 |     88 |      180 |
|    2852 | Galla Karthikeya |     2009 |   290 |     90 |      190 |
|    2852 | Galla Karthikeya |     2010 |   300 |     95 |      200 |
+---------+------------------+----------+-------+--------+----------+
10 rows in set (0.00 sec)


mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM (
    ->     SELECT user_id, user_name
    ->     FROM Account
    ->     WHERE user_id = 3032
    -> ) AS a
    -> JOIN (
    ->     SELECT user_id, photo_id, likes, shares, comments
    ->     FROM facebook
    -> ) AS f ON a.user_id = f.user_id;
+---------+--------------------+----------+-------+--------+----------+
| user_id | user_name          | photo_id | likes | shares | comments |
+---------+--------------------+----------+-------+--------+----------+
|    3032 | Putta Ganesh Kumar |     3001 |   160 |     45 |      110 |
|    3032 | Putta Ganesh Kumar |     3002 |   140 |     40 |      100 |
|    3032 | Putta Ganesh Kumar |     3003 |   180 |     50 |      120 |
|    3032 | Putta Ganesh Kumar |     3004 |   200 |     55 |      130 |
|    3032 | Putta Ganesh Kumar |     3005 |   190 |     52 |      125 |
|    3032 | Putta Ganesh Kumar |     3006 |   170 |     48 |      115 |
|    3032 | Putta Ganesh Kumar |     3007 |   210 |     60 |      135 |
|    3032 | Putta Ganesh Kumar |     3008 |   220 |     65 |      145 |
|    3032 | Putta Ganesh Kumar |     3009 |   230 |     68 |      155 |
|    3032 | Putta Ganesh Kumar |     3010 |   240 |     70 |      165 |
+---------+--------------------+----------+-------+--------+----------+
10 rows in set (0.00 sec)


mysql> SELECT a.user_id, a.user_name, f.photo_id, f.likes, f.shares, f.comments
    -> FROM Account AS a
    -> JOIN facebook AS f ON a.user_id = f.user_id
    -> WHERE f.likes > 200;
+---------+-----------------------+----------+-------+--------+----------+
| user_id | user_name             | photo_id | likes | shares | comments |
+---------+-----------------------+----------+-------+--------+----------+
|    2442 | Nallam Nikhil Reddy   |     1008 |   210 |     78 |      123 |
|    2442 | Nallam Nikhil Reddy   |     1009 |   250 |     80 |      147 |
|    2442 | Nallam Nikhil Reddy   |     1010 |   270 |     89 |      180 |
|    2852 | Galla Karthikeya      |     2001 |   220 |     60 |      130 |
|    2852 | Galla Karthikeya      |     2002 |   210 |     55 |      125 |
|    2852 | Galla Karthikeya      |     2003 |   240 |     70 |      140 |
|    2852 | Galla Karthikeya      |     2004 |   250 |     75 |      150 |
|    2852 | Galla Karthikeya      |     2005 |   230 |     68 |      145 |
|    2852 | Galla Karthikeya      |     2006 |   260 |     80 |      160 |
|    2852 | Galla Karthikeya      |     2007 |   270 |     85 |      170 |
|    2852 | Galla Karthikeya      |     2008 |   280 |     88 |      180 |
|    2852 | Galla Karthikeya      |     2009 |   290 |     90 |      190 |
|    2852 | Galla Karthikeya      |     2010 |   300 |     95 |      200 |
|    3032 | Putta Ganesh Kumar    |     3007 |   210 |     60 |      135 |
|    3032 | Putta Ganesh Kumar    |     3008 |   220 |     65 |      145 |
|    3032 | Putta Ganesh Kumar    |     3009 |   230 |     68 |      155 |
|    3032 | Putta Ganesh Kumar    |     3010 |   240 |     70 |      165 |
|    3892 | Gopireddy Manoj Reddy |     4004 |   210 |     65 |      140 |
|    3892 | Gopireddy Manoj Reddy |     4007 |   220 |     70 |      145 |
|    3892 | Gopireddy Manoj Reddy |     4008 |   230 |     72 |      155 |
|    3892 | Gopireddy Manoj Reddy |     4009 |   240 |     75 |      165 |
|    3892 | Gopireddy Manoj Reddy |     4010 |   250 |     80 |      175 |
+---------+-----------------------+----------+-------+--------+----------+
22 rows in set (0.01 sec)


mysql> select count(photo_id) from facebook where user_id = 3892;
+-----------------+
| count(photo_id) |
+-----------------+
|              10 |
+-----------------+
1 row in set (0.02 sec)

mysql> SELECT user_name
    -> FROM Account
    -> WHERE user_id IN (SELECT user_id FROM facebook WHERE likes = (SELECT MAX(likes) FROM facebook));
+------------------+
| user_name        |
+------------------+
| Galla Karthikeya |
+------------------+
1 row in set (0.01 sec)

mysql> SELECT user_name
    -> FROM Account
    -> WHERE user_id IN (SELECT user_id FROM facebook WHERE comments = (SELECT MAX(comments) FROM facebook));
+------------------+
| user_name        |
+------------------+
| Galla Karthikeya |
+------------------+
1 row in set (0.01 sec)

mysql> SELECT user_name
    -> FROM Account
    -> WHERE user_id IN (SELECT user_id FROM facebook WHERE shares = (SELECT MAX(shares) FROM facebook));
+------------------+
| user_name        |
+------------------+
| Galla Karthikeya |
+------------------+
1 row in set (0.00 sec)

mysql> SELECT a.user_name, i.post_id
    -> FROM Account AS a
    -> JOIN insta AS i ON a.user_id = i.user_id
    -> WHERE i.likes = (SELECT MAX(likes) FROM insta);
+--------------------+---------+
| user_name          | post_id |
+--------------------+---------+
| Putta Ganesh Kumar |  303010 |
+--------------------+---------+
1 row in set (0.00 sec)

mysql> SELECT a.user_name, i.post_id
    -> FROM Account AS a
    -> JOIN insta AS i ON a.user_id = i.user_id
    -> WHERE i.likes = (SELECT Min(likes) FROM insta);
+---------------------+---------+
| user_name           | post_id |
+---------------------+---------+
| Nallam Nikhil Reddy |  244006 |
+---------------------+---------+
1 row in set (0.00 sec)

mysql> SELECT user_id, COUNT(post_id) AS post_count
    -> FROM insta
    -> GROUP BY user_id;
+---------+------------+
| user_id | post_count |
+---------+------------+
|    2441 |         10 |
|    2851 |         10 |
|    3031 |         10 |
|    3891 |         10 |
+---------+------------+
4 rows in set (0.01 sec)


