# Описание проекта

*В ходе этого проекта была разработана модель прогнозирования количества заказов такси в аэропортах на следующий час на основе исторических данных. Моя цель в этом проекте - привлечение большего числа водителей в периоды пиковой нагрузки путем оперативного прогнозирования спроса на услуги такси.
Анализ и использование данных помогают нам эффективно распределять ресурсы и обеспечивать быструю и качественную работу нашего такси во время пиковой нагрузки. Благодаря прогнозированию спроса мы можем предвидеть повышенную потребность в такси, что позволяет нам привлекать больше водителей и обеспечивать нашим клиентам быструю и надежную услугу.
Этот проект поможет  оптимизировать работу, улучшить обслуживание клиентов и повысить уровень удовлетворенности как водителей, так и пассажиров. Я уверен(а), что благодаря этой модели мы сможем эффективно управлять процессом и достигать поставленных целей в области такси обслуживания.*

*Основные характеристики модели:*

*Точность прогнозов: значение метрики RMSE на тестовой выборке не превышает 48, что обеспечивает достаточно высокое качество прогнозирования.
Скорость работы: модель способна обрабатывать данные и делать прогнозы оперативно, что позволяет компании быстро реагировать на изменения спроса.
Простота использования: разработанная модель легко интегрируется в процессы управления таксопарком и не требует специальных знаний для ее работы.
Этот проект позволит компании "Чётенькое такси" оптимизировать работу таксопарка, улучшить обслуживание клиентов в периоды пиковой загруженности и привлечь больше водителей для выполнения заказов.*

# Общий вывод

*Загрузила данные.
Проверила пропуск. Пропусков не было.
Поменяла тип столбца 'datetime' int на datetime. Столбец 'datetime' поставила как индекс датафрейма.
Зделала ресемплирование по часам. Построила график.
Получила график скользящего среднего. По графику скользящая средняя растёт. Проверила на стационарность с помощью теста Дики-Фуллера и Квятковского-Филлипса-Шмидта-Шина (“KPSS”)
Гипотезу для теста Дики-Фуллера.
Нулевая гипотеза: ряд имеет единичный корень.
Альтернативная гипотеза: ряд не имеет единичного корня.
Если нулевую гипотезу не удастся отвергнуть,то этот тест может предоставить доказательство того, что ряд нестационарен.
По ADF тесту p-value меньше 0.05(уровня значимости). По тесту отвергаем нулевую гипотезу, то есть ряд стационарный.
По тесту Квятковского-Филлипса-Шмидта-Шина (“KPSS”).
Нулевая гипотеза: процесс является стационарным по тренду.
Альтернативная гипотеза: ряд имеет единичный корень (ряд не является стационарным).
Если нулевую гипотезу не удастся отвергнуть,то этот тест может предоставить доказательство того, что ряд стационарен.
По итогу временоной ряд нестационарен.
Получила график по тренду,сезонностью,остатк(15 дней). По тренду видно, что есть рост по заказам. По сезонности видим что больше всего заказы бывают в начное время.
По ACF графику есть закономерность каждое 24 часа. То есь есть корреляция между первым и 24-ым лагом.По PACF так же.
Исходя из анализа, для обучения получу признаки месяц,день,часы и день недели.
С помощью функции make_features создала признаки для обучения.
Разделиле датасет на трейн. и тест ваборки.
Создала пайплайн с разными моделями.
Использовала RandomizedSearchCV(кросс валидация) получила лучшую модель и RMSE для этой модели на трен. данных.
RandomForestRegressor(max_features='log2', max_leaf_nodes=16))])
Метрика лучшей модели на тренировочной выборке:, 27.3
Время работы 9.36сек.
Сохранила лучшую модель в переменной rf_model
Сделала предсказания на тестовых данных rmse = 45.8, время работы 771мс*
