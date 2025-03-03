
# Домашнее задание к занятию «Микросервисы: принципы»

Вы работаете в крупной компании, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps-специалисту необходимо выдвинуть предложение по организации инфраструктуры для разработки и эксплуатации.

## Задача 1: API Gateway 

Предложите решение для обеспечения реализации API Gateway. Составьте сравнительную таблицу возможностей различных программных решений. На основе таблицы сделайте выбор решения.

Решение должно соответствовать следующим требованиям:
- маршрутизация запросов к нужному сервису на основе конфигурации,
- возможность проверки аутентификационной информации в запросах,
- обеспечение терминации HTTPS.

Обоснуйте свой выбор.

## Ответ: 
Обеспечение безопасной и единой точки входа запросов от клиента и далнейшего проксирования и балансировки между целевыми сервисами,  крайне сложно представить без организации API - шлюза. Благо что сейчас хватает предложений и продуктов, которые можно подобрать относительно требований проекта. Для этого предлагаю проанализировать указанную таблицу:

|Требования| NGINX | Yandex API Gateway | HAProxy | Amazon API Gateway |
|--------|--------|-------|--------------------------|-----------------|
|Маршрутизация на основе конфигурации|	Да |	Да |	Да | Да |
|Аутентификация в запросе|	Да |	Да |	Да | Да |
|Терминация HTTPS|	Да |	Да |	Да | Да |
|Стоимость| Бесплатно | Платно | Бесплатно | Платно | 

- Как видно из таблицы выше, все выбранные программные решения соответствуют предъявленным требованиям. Если рассматривать не большой проект, с маленьким бюджетом и не большой командой, то я бы выбрал Yandex API Gateway, несмотря на финансовую состовляющую в использовании. Он позволяет пользоваться продуктом прямо из коробки и не требует больших затрат по времени для первичной настройки. Если проект крупный и требует тонких настроект марштрутизации трафика, то выбор за NGINX - проверенный временем, стабильный продукт, имеющий обширное сообщество пользователей, позволяющим тонко сконфигурировать работу серсиса относительно предъявляемых требований. 

## Задача 2: Брокер сообщений

Составьте таблицу возможностей различных брокеров сообщений. На основе таблицы сделайте обоснованный выбор решения.

Решение должно соответствовать следующим требованиям:
- поддержка кластеризации для обеспечения надёжности,
- хранение сообщений на диске в процессе доставки,
- высокая скорость работы,
- поддержка различных форматов сообщений,
- разделение прав доступа к различным потокам сообщений,
- простота эксплуатации.

Обоснуйте свой выбор.

## Ответ:

|Брокер сообщений|	Поддержка кластеризации|	Хранение сообщений на диске|	Высокая скорость работы|	Поддержка форматов сообщений|	Разделение прав доступа|	Простота эксплуатации|
|--------------|------------|-------------|-------------|-------------|---------|-----------|
|RabbitMQ|	Да|	Да|	Да|	XML, JSON и другие|	Да|	Высокая|
|NATS|	Да|	Нет |	Да|	JSON, Protobuf, разнообразные форматы |	Да|	Высокая|
|IBM MQ|	Да|	Да|	Да|	Разнообразные форматы|	Да|	Высокая|
|Apache Kafka|	Да|	Да|	Да|	JSON, Avro, и другие|	Да|	Средняя|

- Считаю, что наиболее доступным и отвечающим различным требованиям бизнеса можно назвать MQ Kafka. kafka обеспечивает наибольшую пропускную способность сообщений в системе в секунду, что позволяет передавать большие объемы данных; удобно масштабируемая архитектура, позволяет быстро адаптироваться к увеличению или уменьшению объема передаваемых данных; грануляция прав доступа к сообщениям позволяет произвести тонкую настройку потребителей и продюсеров, тем самым обеспечив большую безопасность канала передачи сообщений; хранение сообщений на диске обеспечивает возможность восстановления данных в случаях сбоя в работе приложения; широко используется на различных проектах, что формирует большое сообщество пользователей и дает возможность накапливать знания и делиться ими.



### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
