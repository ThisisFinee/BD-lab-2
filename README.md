# BD-lab-2
---
## 1 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/1(CREATE)): 
```SQL CREATE DATABASE "Base_lab_2"
    WITH
    OWNER = postgres
    ENCODING = 'UTF8'
    LC_COLLATE = 'Russian_Russia.1251'
    LC_CTYPE = 'Russian_Russia.1251'
	_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
	
CREATE TABLE IF NOT EXISTS public."Место_работы"
(
    "Идентификатор" integer NOT NULL,
    "Название_организации" text COLLATE pg_catalog."default" NOT NULL,
    "Адрес_работы" text COLLATE pg_catalog."default" NOT NULL,
    "Льгота" integer NOT NULL
)
TABLESPACE pg_default;
ALTER TABLE IF EXISTS public."Место_работы"
    OWNER to postgres;
	
CREATE TABLE IF NOT EXISTS public."Автопредприятие"
(
    "Идентификатор" integer NOT NULL,
    "Название" text COLLATE pg_catalog."default" NOT NULL,
    "Расположение" text COLLATE pg_catalog."default" NOT NULL,
    "Комиссионные" integer NOT NULL
)

TABLESPACE pg_default;
ALTER TABLE IF EXISTS public."Автопредприятие"
    OWNER to postgres;
	
CREATE TABLE IF NOT EXISTS public."Техника"
(
    "Идентификатор" integer NOT NULL,
    "Тип" text COLLATE pg_catalog."default" NOT NULL,
    "Адрес_гаража" text COLLATE pg_catalog."default" NOT NULL,
    "Макс_количество" integer NOT NULL,
    "Стоимость_заказа" bigint NOT NULL
)
TABLESPACE pg_default;
ALTER TABLE IF EXISTS public."Техника"
    OWNER to postgres;

CREATE TABLE IF NOT EXISTS public."Заказ"
(
    "Номер" integer NOT NULL,
    "Дата" text COLLATE pg_catalog."default" NOT NULL,
    "Место_работы" integer NOT NULL,
    "Автопредприятие" integer NOT NULL,
    "Техника" integer NOT NULL,
    "Количество" integer NOT NULL,
    "Оплата" bigint NOT NULL
)
TABLESPACE pg_default;
ALTER TABLE IF EXISTS public."Заказ"
    OWNER to postgres;
```
### [Результат](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/1%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png):
![ZAP1](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/1%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png)

---

## 2 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/2(INSERT)):
```SQL
INSERT INTO public."Место_работы"( "Идентификатор", "Название_организации", "Адрес_работы", "Льгота")
	VALUES (001, 'Песочный карьер 8', 'Бор', 0);
INSERT INTO public."Место_работы"( "Идентификатор", "Название_организации", "Адрес_работы", "Льгота")
	VALUES (002, 'Овощная база',	'Ильино', 5);
INSERT INTO public."Место_работы"( "Идентификатор", "Название_организации", "Адрес_работы", "Льгота")
	VALUES (003, 'ТЭЦ', 'Джержинск', 5);
INSERT INTO public."Место_работы"( "Идентификатор", "Название_организации", "Адрес_работы", "Льгота")
	VALUES (004, 'Детский сад 1', 'Н.Новгород',	10);
INSERT INTO public."Место_работы"( "Идентификатор", "Название_организации", "Адрес_работы", "Льгота")
	VALUES (005, 'Стройплощадка 15', 'Н.Новгород', 0);
	
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (001, 'АТП 12', 'Н.Новгород', 7);
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (002, 'МП АВто', 'Джержинск', 6);
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (003, 'АТП 9', 'Ильино',	6);
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (004, 'АТП 7', 'Кстово',	4);
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (005, 'АТП 3', 'Н.Новгород', 7);
INSERT INTO public."Автопредприятие"( "Идентификатор", "Название", "Расположение", "Комиссионные")
	VALUES (006, 'Борский автоотряд', 'Бор', 4);
	
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (001, 'Грузовая_машина',	'Н.Новгород', 10, 100000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (002, 'Автобус',	'Н.Новгород', 5, 200000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (003, 'Цистерна', 'Ильино', 4, 110000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (004, 'Автокран', 'Бор', 3, 160000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (005, 'Бетономешалка', 'Бор', 3, 130000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (006, 'Самосвал', 'Кстово', 5, 100000);
INSERT INTO public."Техника"("Идентификатор", "Тип", "Адрес_гаража", "Макс_количество", "Стоимость_заказа")
	VALUES (007, 'Автофургон', 'Джержинск', 15, 100000);

INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00000, 'Понедельник', 001, 003,	007, 1, 100000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00001, 'Понедельник', 001, 005,	007, 2, 200000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00002, 'Понедельник', 003, 002, 007, 1, 100000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00003, 'Понедельник', 004, 003, 007, 1, 100000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00004, 'Вторник', 005, 004, 002, 2, 400000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00005, 'Среда',	001, 006, 004, 1, 160000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00006, 'Среда', 001, 004, 004, 1, 160000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00007, 'Среда', 004, 001, 004, 1, 160000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00008, 'Четверг', 002, 004,	003, 1, 110000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00009, 'Четверг', 002, 005, 002, 1, 200000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00010, 'Четверг', 004, 001,	006, 2, 200000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00011, 'Четверг', 005, 003, 005, 1, 200000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00012, 'Пятница', 004, 002,	001, 4,	400000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00013, 'Пятница', 004, 005, 001, 1, 100000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00014, 'Пятница', 004, 004, 001, 3, 300000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00015, 'Пятница', 005, 006, 006, 2, 200000);
INSERT INTO public."Заказ"("Номер", "Дата", "Место_работы", "Автопредприятие", "Техника", "Количество", "Оплата")
	VALUES (00016, 'Суббота', 002, 001, 001, 4, 400000);
  ```
  ### [Результат](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/2%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png)
  Insert 0 1
  
  ---
  
  ## 3 Задание
  ### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/3(SELECT)):
  ```SQL
SELECT * FROM public."Место_работы";

SELECT * FROM public."Автопредприятие";

SELECT * FROM public."Техника";

SELECT * FROM public."Заказ";
```
### [Результат](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/3%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png):
![zap3](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/3%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png)

---

## 4 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4(SELECT(c,d,e))):
```SQL
--c):
SELECT Название_организации, Льгота FROM Место_работы;
--d):
SELECT Расположение FROM Автопредприятие;
--e):
SELECT Адрес_гаража FROM Техника;
```
### Результат [c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png), [d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png), [e](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(e).png):
#### C:
![zap4c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png)
#### D:
![zap4d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png)
#### E:
![zap4e](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/4%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(e).png)

---

## Задание 5
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5(SELECT,WHERE)):
```SQL
--c):
SELECT Тип,Адрес_гаража FROM Техника WHERE Макс_количество > 3 ;
--d):
SELECT Название, Комиссионные FROM Автопредприятие WHERE Комиссионные>5 AND Расположение!= 'Н.Новгород'
ORDER BY Комиссионные ASC;
--e):
SELECT Название_организации FROM Место_работы WHERE Адрес_работы = 'Ильино';
```
### Результат [c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png), [d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png), [e](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(e).png):
#### C:
![zap5c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png)
#### D:
![zap5d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png)
#### E:
![zap5e](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/5%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(e).png)

---

## Задание 6
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/6(SELECT,JOIN)):
```SQL
--c):
SELECT Название_организации, Тип, Количество, Оплата
FROM Заказ
JOIN Место_работы ON Заказ.Место_работы = Место_работы.Идентификатор
JOIN Техника ON Заказ.Техника = Техника.Идентификатор
ORDER BY Оплата ASC, Заказ.Место_работы ASC;
--d):
SELECT Номер, Дата, Название
FROM Заказ
JOIN Автопредприятие ON Заказ.Автопредприятие = Автопредприятие.Идентификатор;
```
### Результат [c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/6%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png), [d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/6%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png):
#### C:
![zap6c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/6%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png)
#### D:
![zap6d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/6%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png)

---

## 7 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7(I%20HATE%20THIS)):
```SQL
--c):
SELECT Название, Название_организации, Адрес_работы
FROM Заказ
JOIN Автопредприятие ON Заказ.Автопредприятие = Автопредприятие.Идентификатор
JOIN Место_работы ON Заказ.Место_работы = Место_работы.Идентификатор
WHERE Место_работы.Льгота >= 3 and Место_работы.Адрес_работы != Автопредприятие.Расположение;
--d):
SELECT Техника.Идентификатор, Тип
FROM Заказ
JOIN Автопредприятие ON Заказ.Автопредприятие = Автопредприятие.Идентификатор
JOIN Техника ON Заказ.Техника = Техника.Идентификатор
WHERE Автопредприятие.Расположение = Техника.Адрес_гаража;
--f):
SELECT Название_организации
FROM Заказ
JOIN Место_работы ON Заказ.Место_работы = Место_работы.Идентификатор
WHERE Оплата > 100000;
```
### Результат [c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png), [d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png), [f](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(f).png)
#### C:
![zap7c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png)
#### D:
![zap7d](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(d).png)
#### F:
![zap7f](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/7%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(f).png)

---

## 8 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/8(Update)):
```SQL
--8:
UPDATE Заказ
SET Оплата = Оплата - ((Оплата/100) * (SELECT Льгота FROM Место_работы WHERE Место_работы.Идентификатор = Заказ.Место_работы));
SELECT Оплата FROM Заказ;
```
### [Результат](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/8%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png):
![zap8](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/8%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png)

---

## 9 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/9(ALTER%20TABLE)):
```SQL
--9	
ALTER TABLE IF EXISTS public."Заказ"
    ADD COLUMN "Величина_комиссионных" bigint;

Update Заказ
SET Величина_комиссионных = Оплата/100*(SELECT Комиссионные FROM Автопредприятие WHERE Заказ.Автопредприятие = Автопредприятие.Идентификатор);

ALTER TABLE IF EXISTS public."Заказ"
    ALTER COLUMN "Величина_комиссионных" SET NOT NULL;
```
### [Результат](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/9%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png):
![zap9](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/9%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81.png)

---

## 10 Задание
### [Код](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/10):
```SQL
--c):
SELECT Название_организации FROM Заказ
JOIN Место_работы ON Заказ.Место_работы = Место_работы.Идентификатор
JOIN Техника ON Заказ.Техника = Техника.Идентификатор
WHERE Техника.Адрес_гаража NOT IN ('Н.Новгород')
```
 ### Результат [с](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/10%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png):
 ![zap10c](https://github.com/ThisisFinee/BD-lab-2/blob/22ba4b2601e69df06bd9ac439ce3f8399be74b7b/10%20%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81(c).png)
 
