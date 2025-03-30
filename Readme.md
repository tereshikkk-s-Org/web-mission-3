# Mission 3

## Part 1

> [Видео](https://drive.google.com/file/d/1eg4qiuC0l8idB0g-g3x2HWGsXafuMw34/view?usp=sharing)

## Part 2

> [Видео](https://drive.google.com/file/d/1f4t_J8XTFKaIQzadEIbd6ZErDAlniA_M/view?usp=sharing)

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
