# SQL_-
# Создайте функцию, которая принимает кол-во сек и формат их в кол-во дней часов.
# Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '

DELIMITER $$
DROP PROCEDURE IF EXISTS seconds_to_text;
CREATE PROCEDURE seconds_to_text(seconds INT)
BEGIN
    DECLARE days INT default 0;
    DECLARE hours INT default 0;
    DECLARE minutes INT default 0;

    SET days = seconds / 86400;
    SET seconds = seconds % 86400;
  
    SET hours = seconds / 3600;
    SET seconds = seconds % 3600;

    SET minutes = seconds / 60;
    SET seconds = seconds % 60;

SELECT seconds AS seconds_INT, CONCAT 
(
  days, ' days ',
  hours, ' hours ',
  minutes, ' minutes ',
  seconds, ' seconds'
) AS seconds_to_text;
END $$
DELIMITER ;

CALL seconds_to_text(16);

# Выведите только четные числа от 1 до 10. Пример: 2,4,6,8,10

DELIMITER $$
DROP PROCEDURE IF EXISTS numbers;
CREATE PROCEDURE numbers(n INT)
BEGIN
    DECLARE result VARCHAR(255) DEFAULT '';
    DECLARE current_number INT DEFAULT 2;

    WHILE current_number <= n DO
        SET result = CONCAT(result, current_number, ' ');
        SET current_number = current_number + 2;
    END WHILE;
SELECT result AS numbers, CONCAT 
(
  result, ''
) AS numbers;    

END $$

DELIMITER ;
CALL numbers(10);
