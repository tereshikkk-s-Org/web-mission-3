# Mission 3

## Part 1

- Данные для проверки работы 
> (https://8b7si3.buildship.run/me)
```json
{
  "password": "admin",
  "username": "admin"
}
```
> [Скрин буилдшипа]([https://drive.google.com/file/d/1q8mOOZY584GQDueKdjzIIke_v5OqRPU_/view?usp=sharing](https://docs.google.com/document/d/1o-Jr56dm3gv0kHCwplex3QjXYw1dEn8FLc13U6z79v4/edit?usp=sharing))

## Part 2

- Данные для проверки работы 
> (https://8b7si3.buildship.run/me](https://8b7si3.buildship.run/message)
```json
{
  "password": "admin",
  "message": {
    "text": "hi",
    "to": "elya"
  },
  "username": "admin"
}
```
> [Скрин буилдшипа]([https://drive.google.com/file/d/1q8mOOZY584GQDueKdjzIIke_v5OqRPU_/view?usp=sharing](https://docs.google.com/document/d/1o-Jr56dm3gv0kHCwplex3QjXYw1dEn8FLc13U6z79v4/edit?usp=sharing))

## Part 3

- Запрос 1

```sql
SELECT username FROM users
```

- Запрос 2

```sql
SELECT 
    users.username, 
    COUNT(messages.id) AS number_of_sent_messages
FROM 
    users
LEFT JOIN 
    messages ON users.id = messages.from
GROUP BY 
    users.username
```

- Запрос 3

```sql
SELECT 
    users.username, 
    COUNT(messages.id) AS number_of_received_messages
FROM 
    users
JOIN 
    messages ON users.id = messages.to
GROUP BY 
    users.username
ORDER BY 
    number_of_received_messages DESC
LIMIT 1
```

- Запрос 4

```sql
SELECT AVG(message_count) AS average_messages_sent
FROM (
    SELECT COUNT(messages.id) AS message_count 
    FROM users 
    LEFT JOIN messages ON users.id = messages.from 
    GROUP BY username
) AS subquery
```
