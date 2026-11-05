# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor User as Пользователь
    participant App as Веб-приложение
    participant API as API сервиса
    participant Model as ML-модель
    participant DB as База данных

    User->>App: Ввести текст отзыва
    User->>App: Нажать «Проанализировать»
    App->>API: Отправить текст отзыва
    API->>Model: Передать текст для классификации
    Model-->>API: Вернуть тональность и уверенность
    API->>DB: Сохранить результат анализа
    API-->>App: Вернуть результат
    App-->>User: Показать тональность и уверенность
```

## Диаграмма классов

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +string email
    }

    class Review {
        +int id
        +string text
        +datetime createdAt
    }

    class SentimentAnalysis {
        +int id
        +string sentiment
        +float confidence
        +datetime analyzedAt
    }

    class MLModel {
        +string modelName
        +string version
        +analyze(text) SentimentAnalysis
    }

    User "1" --> "*" Review
    Review "1" --> "1" SentimentAnalysis
    MLModel "1" --> "*" SentimentAnalysis
```