Домашнее задание к занятию «SQL. Часть 1» - `Уткин Евгений`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

фамилия и имя сотрудника из этого магазина;
город нахождения магазина;
количество пользователей, закреплённых в этом магазине.

```
SELECT st.first_name AS Имя, st.last_name AS Фамилия, a.address AS адрес, COUNT(c.store_id) AS Покупки 
FROM customer c
JOIN store s ON c.store_id = s.store_id
JOIN staff st ON s.manager_staff_id = st.staff_id 
JOIN address a ON s.store_id = a.address_id
GROUP BY c.store_id
HAVING Покупки > 300

```

![Задание №1](https://github.com/newDjon/hw-03/blob/main/store.png)


---

### Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

```
SELECT COUNT(1) AS big_films
FROM film f 
WHERE length > (SELECT AVG(length) from film)

```

![Задание №2](https://github.com/newDjon/hw-03/blob/main/film.png)

---

### Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

```
SELECT MONTH(payment_date) AS data, COUNT(payment_id) AS count_pay, SUM(amount) AS amount
FROM payment
GROUP BY MONTH(payment_date) 
ORDER BY count_pay DESC LIMIT 1

```

![Задание №3](https://github.com/newDjon/hw-03/blob/main/count_pay.png)

---










 

 








