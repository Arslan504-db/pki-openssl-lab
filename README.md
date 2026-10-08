# Развёртывание PKI и управление сертификатами на OpenSSL

Курсовая работа по дисциплине «Методы и средства криптографической защиты информации». Направление 10.03.01 «Информационная безопасность».

## 🎯 Задача

Развернуть учебную инфраструктуру открытых ключей (PKI) на OpenSSL и изучить полный жизненный цикл цифровых сертификатов.

## 🛠 Что реализовано

- **Установка и настройка OpenSSL** в Windows 11
- **Создание корневого удостоверяющего центра (Root CA)**
  - Генерация ключа RSA 4096 бит
  - Самоподписанный сертификат X.509 сроком на 10 лет
- **Создание промежуточного CA (Intermediate CA)**
  - Генерация ключа и CSR
  - Подписание CSR корневым CA с расширением `v3_intermediate_ca`
- **Выпуск сертификата для веб-сервера**
  - Генерация ключа и CSR
  - Подписание промежуточным CA
  - Формирование цепочки сертификатов
- **Проверка цепочки доверия** (`openssl verify`)
- **Отзыв сертификата и работа с CRL**

## 🧰 Стек

```
OpenSSL 3.6  |  Windows 11  |  PKI
X.509        |  RSA 4096    |  SHA-256
```

## 📊 Структура PKI

```
PKI_Lab/
├── root_ca/              # Корневой CA
│   ├── private/          # Закрытый ключ
│   ├── certs/            # Сертификат
│   └── crl/              # Списки отзыва
├── intermediate_ca/      # Промежуточный CA
│   ├── private/
│   ├── certs/
│   └── crl/
└── end_entities/         # Конечные субъекты
    ├── server.key
    ├── server.csr
    └── server.crt
```

## 📸 Доказательства

### Установка и проверка OpenSSL
![OpenSSL](https://raw.githubusercontent.com/Arslan504-db/pki-openssl-lab/main/screenshot_openssl.png)

### Создание сертификата Root CA
![Root CA](https://raw.githubusercontent.com/Arslan504-db/pki-openssl-lab/main/screenshot_root_ca.png)

### Проверка цепочки доверия
![Verify](https://raw.githubusercontent.com/Arslan504-db/pki-openssl-lab/main/screenshot_verify.png)

## 📚 Что я узнал

- Как устроен сертификат **X.509** (структура, поля, расширения)
- Как работает **цепочка доверия** в PKI
- Как развернуть **собственный CA** на OpenSSL
- Как **отзывать сертификаты** через CRL
- Чем отличается **Root CA** от **Intermediate CA**
- Как обеспечить безопасность ключей (шифрование, HSM)

## 🔗 Связанные проекты

- [Мини-SIEM на ELK](https://github.com/Arslan504-db/diploma-siem-education)
- [Мониторинг сетевого трафика](https://github.com/Arslan504-db/network-traffic-monitoring)
- [Пентест-лаборатория](https://github.com/Arslan504-db/pentest-lab-report)
