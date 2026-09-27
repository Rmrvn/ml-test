# Avito: кандидатогенерация для поиска услуг
.

## Задача

По короткому поисковому запросу отобрать из корпуса ~189 тыс. объявлений
услуг до 50 кандидатов-объявлений для последующего этапа ранжирования.
Метрика — Recall@50.

## Решение

Лексический поиск: word-level TF-IDF (стемминг + max_df + sublinear_tf)
+ эвристические бусты по микрокатегории и локации + fallback для edge cases.
Recall@50 на held-out валидации (5% запросов train): **0.7661**.

Полное описание подхода, EDA, экспериментов и анализа ошибок — в
[`solution.ipynb`](./solution.ipynb) (раздел "Summary" в начале ноутбука).

## Как воспроизвести

1. Установить зависимости: `pip install -r requirements.txt`
2. Скачать `train.parquet`, `benchmark_queries.parquet`, `benchmark_items.parquet`
   и положить в папку `data/`
3. Открыть `solution.ipynb`, `Restart & Run All`
4. Результат сохранится в `answer.csv`

## Используемые открытые библиотеки

- scikit-learn (TfidfVectorizer) — MIT-подобная лицензия (BSD)
- nltk (SnowballStemmer, русский язык) — Apache 2.0

## Итоговая метрика

Recall@50 на валидации: 0.7661