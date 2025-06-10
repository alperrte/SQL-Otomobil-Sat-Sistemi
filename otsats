CREATE DATABASE IF NOT EXISTS OtomobilSatisSistemi;
USE OtomobilSatisSistemi;

CREATE TABLE IF NOT EXISTS `Musteriler` (
    `musteri_id` INT AUTO_INCREMENT,
    `ad` VARCHAR(50) NOT NULL,
    `soyad` VARCHAR(50) NOT NULL,
    `email` VARCHAR(100) NOT NULL,
    `telefon` VARCHAR(15) NOT NULL,
    PRIMARY KEY (`musteri_id`)
);

CREATE TABLE IF NOT EXISTS `Araclar` (
    `arac_id` INT AUTO_INCREMENT,
    `model` VARCHAR(100) NOT NULL,
    `uretim_yili` YEAR NOT NULL,
    `fiyat` DECIMAL(10,2) NOT NULL,
    `kilometre` INT NOT NULL,
    PRIMARY KEY (`arac_id`)
);

CREATE TABLE IF NOT EXISTS `Satislar` (
    `satis_id` INT AUTO_INCREMENT,
    `arac_id` INT,
    `musteri_id` INT,
    `satis_tarihi` DATE,
    PRIMARY KEY (`satis_id`),
    FOREIGN KEY (`arac_id`) REFERENCES `Araclar`(`arac_id`),
    FOREIGN KEY (`musteri_id`) REFERENCES `Musteriler`(`musteri_id`)
);

INSERT INTO `Musteriler` (`ad`, `soyad`, `email`, `telefon`)
VALUES
('Serhat', 'İnci', 'serhat.inci@hotmail.com', '5431291516'),
('Sinan', 'Koç', 'sinan.koc12@outlook.com', '5302566517'),
('Muhittin', 'Kale', 'kale.muho@gmail.com', '5362174893'),
('Halil', 'Kapa', 'halilkap@gmail.com', '5391048257'),
('Engin', 'Kahale', 'enginkahale@gmail.com', '5326984712'),
('Hayri', 'Turat', 'tur.athayri74@outlook.com', '5302566517'),
('Sinan', 'Engin', 'engin.sinan@hotmail.com', '5431291516'),
('Sinan', 'Koç', 'sinan.koc12@hotmail.com', '5351204876'),
('Serhat', 'İnci', 'serhat.inci@outlook.com', '5305897234'),
('Mehmet', 'Öztürk', 'mehmet.ozturk96@outlook.com', '5532146696');

INSERT INTO `Araclar` (`model`, `uretim_yili`, `fiyat`, `kilometre`)
VALUES 
('Toyota Corolla', 2018, 775000.00, 30000),
('Honda Civic', 2019, 945000.00, 5000),
('Volkswagen Golf', 2017, 685000.00, 40000),
('BMW 3 Series', 2021, 1495000.00, 15000),
('Mercedes-Benz C-Class', 2018, 1150000.00, 20000),
('Audi A4', 2020, 995000.00, 10000),
('Renault Megane', 1999, 315000.00, 500000),
('Hyundai Elantra', 2016, 645000.00, 60000),
('Peugeot 308', 2004, 270000.00, 210000),
('Ford Focus', 2020, 749000.00, 100000);

INSERT INTO `Satislar` (`arac_id`, `musteri_id`, `satis_tarihi`)
VALUES
(1, 1, '2022-11-01'),
(2, 5, '2020-09-06'),
(3, 8, '2023-02-11'),
(4, 3, '2024-05-15'),
(5, 7, '2024-08-25'),
(6, 9, '2021-10-03'),
(7, 4, '2019-07-19'),
(8, 2, '2021-06-21'),
(9, 6, '2021-03-13'),
(10, 1, '2023-04-28');


SELECT ad, soyad FROM Musteriler
WHERE ad LIKE '%A%' OR soyad LIKE '%A%';

SELECT * FROM Satislar
WHERE YEAR(satis_tarihi) <= 2024;

SELECT * FROM Araclar
WHERE uretim_yili IN (2018, 2020);

SELECT * FROM Araclar
WHERE fiyat BETWEEN 500000 AND 1000000;

SELECT araclar.model, araclar.kilometre FROM Araclar 
JOIN Satislar ON araclar.arac_id = satislar.arac_id;

SELECT * FROM Satislar
ORDER BY satis_tarihi ASC
LIMIT 4;

SELECT * FROM Araclar
WHERE kilometre > 50000;

SELECT * FROM Satislar
JOIN Araclar ON Satislar.arac_id = Araclar.arac_id
WHERE Araclar.model LIKE '%Toyota%';

SELECT * FROM Araclar
WHERE fiyat > 100000;

SELECT musteri_id, COUNT(*) AS arac_sayisi
FROM Satislar
GROUP BY musteri_id;

SELECT * FROM Araclar
WHERE uretim_yili > 2020;

SELECT * FROM Araclar
WHERE fiyat > 200000
ORDER BY fiyat DESC
LIMIT 2;

SELECT * FROM Araclar
ORDER BY kilometre DESC
LIMIT 5;

SELECT * FROM Araclar
WHERE uretim_yili = 2020
AND arac_id IN (SELECT arac_id FROM Satislar);

SELECT * FROM Satislar
WHERE musteri_id = 4;

SELECT musteri_id FROM Satislar
GROUP BY musteri_id
HAVING COUNT(*) = 1;

SELECT satislar.satis_tarihi, araclar.model
FROM Satislar 
JOIN Araclar  ON satislar.arac_id = araclar.arac_id
WHERE araclar.fiyat BETWEEN 500000 AND 800000;

SELECT musteriler.ad, musteriler.soyad, araclar.model
FROM Musteriler 
JOIN Satislar  ON musteriler.musteri_id = satislar.musteri_id
JOIN Araclar  ON satislar.arac_id = araclar.arac_id
WHERE araclar.uretim_yili IN (2018, 2019);

SELECT * FROM Araclar
WHERE kilometre < 10000;

SELECT araclar.model, araclar.fiyat
FROM Satislar 
JOIN Araclar  ON satislar.arac_id = araclar.arac_id
ORDER BY satislar.satis_tarihi DESC
LIMIT 2;

SELECT * FROM Araclar
WHERE uretim_yili = 2004
AND arac_id IN (SELECT arac_id FROM Satislar);

SELECT * FROM Musteriler
WHERE ad = 'Sinan';

SELECT musteriler.ad, musteriler.soyad, araclar.model, araclar.fiyat
FROM Musteriler 
JOIN Satislar  ON musteriler.musteri_id = satislar.musteri_id
JOIN Araclar  ON satislar.arac_id = araclar.arac_id
WHERE araclar.fiyat > 1000000;

SELECT * FROM Araclar
WHERE fiyat < 1500000
AND uretim_yili = 2021;

SELECT * FROM Araclar
WHERE kilometre < 30000;
