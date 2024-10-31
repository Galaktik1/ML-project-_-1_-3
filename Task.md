# ML-project • Фаза 1 • Неделя 3
## Классические алгоритмы ML • Machine Learning

### Проект: предсказание цен на недвижимость

* [Описание задачи](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

* Проект будет состоять из нескольких блоков с заданиями:

1. Загрузить результаты на сайт [kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques) и получить как можно более точную оценку качества твоих предсказаний! Это соревнование, а значит есть лидерборд данного соревнования [здесь](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/leaderboard)
    
2. Построить и задеплоить ML-сервис для автоматического предсказания будущих объектов недвижимости в этом районе. Сделать это необходимо с помощью [streamlit](streamlit.io). Необходимо:
    - Пользователь имел интерфейс подгрузки через файл и получал оценку стоимости для объектов.
    - Файл будет подаваться с исходными фичами до препроцессинга, ваш пайплайн его должен обработать и выдать предикт. 

3. Подготовить небольшую презентацию, либо оформить как streamlit-страницу итогов исследования:
    - Какие идеи пробовали по фича-инжинирингу, удаление ненужных столбцов и так далее
    - Какой пайплайн оказался самым удачным
    - Графическую оценку важности ключевых признаков(shap, feature_importance, permutation_importance, и т.д.)
    - Таблицу(строка: модели, столбец: метрики) с результатами по ключевым метрикам качества(rmse, mae, r2_score, rmlse) на кросс-валидации
    - Итоговое соревновательное место на kaggle


### 🗓 План действий может быть таким:

- __первый день__:

    1. Загрузи три файла: `train.csv` (с таргетом) и `test.csv` (без таргета, предсказания по ней необходимо отправить на kaggle), а также файл `submission.csv` - это шаблон для твоих ответов. 
    2. Сделай базовую визуализацию, чтобы с чего-то начать: распределение цен на дома (таргета), сабплот с гистограмами числовых признаков, сабплот с барплотами категориальных признаков, матрица корреляций.
    4. Так как метрика качества RMLSE, рекомендуется обучать модель не на таргете, а на логарифме таргета, это должно дать большую точность. Да и если прологарифмировать таргет, то его распределение становится нормальным.
    5. Объедини обучающую и тестовую выборку в единый датафрейм, и начинать собирать препроцессор.
    6. Произведи предобработку данных:
        - удали/заполни пропуски
        - подумай, что сделать с категориальными переменными (**обязательно** изучи все признаки и их описания [тут](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data))
        - При необходимости нормировка данных
    7. Раздели обучающую и тестовую части выборки обратно
    8. Построй __baseline модель__: соберите самый простой пайплайн, сделай предсказания и запиши результат в `submission.csv`
    9. Загрузи результат на [kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/submit)
    10. Полученный на шаге 7 результат необходимо максимально улучшить! Помни, что число попыток на `kaggle` ограничено. 

- __второй день__
    1. Попытка улучшить бейзлайн модель первого дня
        - Удаление бесполезных столбцов
        - Создание новых(__feature engineering__)
        - Попытки борьбы с мультиколлинеарностями(PCA, удаление)
        - И так далее
    2. Тюнинг моделей
    3. Деплой модели и создание ML-сервиса
    4. Подготовка презентации


### Советы

📌В первую очередь __обязательно__ изучите все признаки и их описания есть в файле `description.txt`. Это поможет для правильного препроцессинга признаков и понимания задачи

📌Стремитесь не усложнять, а упрощать свои пайплайны.

📌Грамотно разделите обязанности в команде. Кто-то отвечает за заполнение пропусков, кто-то за кодирование данных, выбирая где и какой encoder лучше подойдет. Кто-то пытается сгенрировать новые фичи

📌Старайтесь все описывать функционально или через трансформеры, чтобы после собирать общий командный пайплайн.

📌Так как метрика качества на kaggle RMLSE, рекомендуется обучать модель не на таргете, а на логарифме таргета, это должно дать большую точность. Обучаем на логарифме -> Предсказываем логарифм ->  делаем обратный откат(np.exp) -> загрузка на  kaggle

📌 В процессе работы комментируй результаты и делай разделы в ноутбуке с помощью markdown. Это поможет выдерживать структуру файла и не запутаться.

