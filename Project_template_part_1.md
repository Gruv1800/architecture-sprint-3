# Задание 1. Анализ и планирование

### 1. Описание функциональности монолитного приложения

**Управление отоплением:**
- Пользователи могут включать\отключать отопление;
- Пользователи могут регулировать температуру;
- Система поддерживает получение текущего состояния отопительной системы (включена\выключена).

**Мониторинг температуры:**
- Пользователи могут регулировать температурный режим;
- Система поддерживает получение текущих температурных показателей с датчиков;
- Система поддерживает регистрацию новых датчиков в системе.

### 2. Анализ архитектуры монолитного приложения

- **Язык программирования**: Java;
- **База данных**: PostgreSQL;
- **Архитектура**: Монолитная, все компоненты системы (обработка запросов, бизнес-логика, работа с данными) находятся в рамках одного приложения;
- **Взаимодействие**: Синхронное, запросы обрабатываются последовательно;
- **Масштабируемость**: Ограничена, так как монолит сложно масштабировать по частям;
- **Развёртывание**: Требует остановки всего приложения. Downtime ~ 5-7 минут.

### 3. Определение доменов и границы контекстов

- **Домен управления устройствами**. Данный домен отвечает за добавление\удаление устройств в систему, изменение параметров и включение\выключение;
- **Домен мониторинга**. С заданной периодичностью опрашивает устройства, собирает метрики, предоставляет дашборды и графики для оценки состояния устройств;
- **Домен уведомлений**. Рассылка оповещений пользователям системы;
- **Домен учетных данных**. Предоставляет аутентификацию, авторизацию и хранение информации о пользователях, зарегистрированных в системе;
- **Домен тех. поддержки**. Заведение заявок в систему, поддержка пользователей.
- **Домен оплаты**. Предоставляет возможность оплаты услуг.

### **4. Проблемы монолитного решения**

- **Масштабируемость**: отсутствует возможность масштабирования отдельных компонентов системы;
- **Сложность релизов**: приходится согласовывать релиз со всеми командами, разрабатывающими монолитную систему;
- **Снижение скорости поставки новых фич**: следствие из пункта выше;
- **Надежность**: при любом сбое системы выходит из строя целиком (компоненты не доступны по отдельности).


### 5. Визуализация контекста системы — диаграмма С4

[monolit_c4_context.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/monolit_c4_context.puml)

[monolit_c4_context.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/monolit_c4_context.png)


# Задание 2. Проектирование микросервисной архитектуры

**Диаграмма контейнеров (Containers)**

[microservices_c4_container.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_container.puml)

[microservices_c4_container.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_container.png)

**Диаграмма компонентов (Components)**

Auth

[microservices_c4_auth_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_auth_component.puml)

[microservices_c4_auth_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_auth_component.png)

Device Management

[microservices_c4_dm_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_dm_component.puml)

[microservices_c4_dm_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_dm_component.png)

Monitoring

[microservices_c4_monitoring_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_monitoring_component.puml)

[microservices_c4_monitoring_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_monitoring_component.png)

Notification

[microservices_c4_notification_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_notification_component.puml)

[microservices_c4_notification_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_notification_component.png)

Payments

[microservices_c4_payment_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_payment_component.puml)

[microservices_c4_payment_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_payment_component.png)

Support

[microservices_c4_support_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_support_component.puml)

[microservices_c4_support_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_support_component.png)

Telemetry

[microservices_c4_telemetry_component.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_telemetry_component.puml)

[microservices_c4_telemetry_component.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_telemetry_component.png)

**Диаграмма кода (Code)**

[microservices_c4_code.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_code.puml)

[microservices_c4_code.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_c4_code.png)



# Задание 3. Разработка ER-диаграммы

[microservices_er_diagram.puml](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_er_diagram.puml)

[microservices_er_diagram.png](https://github.com/Gruv1800/architecture-sprint-3/blob/sprint_3/diagrams/microservices_er_diagram.png)
