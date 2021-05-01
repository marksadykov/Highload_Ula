# Курсовая работа по дисциплине: Проектирование высоконагруженных систем (Highload_Ula).
## Тема: Юла

### Целевая аудитория

#### Распределение аудитории
| Страна      | Процент аудитории |  Количество пользователей в месяц   | Количество пользователей в день |
| :---        |    :----:   |        :----:   | ---:|
| Россия      | 85,9%       | 23 193 000   | 773 100 |
| Германия   | 4,3%       | 1 161 000      | 38 700 |
| Великобритания   | 	2,3%        | 621 000      | 20 700 |

- Количество активных пользователей в месяц: 27 млн человек.
- Средний возраст пользователей: от 18 до 35 лет.


#### Поведение пользователей (в рамках дня)
| Время на сайте      | Количество страниц за посещение | Количество размещений |  Отказы   |
| :---        |    :----:   |        :----:   | ---:|
| 7 минут | 6       | 0.25 | 42% |

### Расчет нагрузки

1) Оценка количества новых пользователей в день.
   ![stat](stat.png)
   - Рассмотрим количество пользователей в последние 6 месяцев
     
        | Октябрь<span style="color:white">__</span>| Ноябрь<span style="color:white">___</span> | Декабрь<span style="color:white">__</span> |  Января<span style="color:white">___</span>   | Февраль<span style="color:white">__</span>   | Март<span style="color:white">_____</span>  |
        | :---        |    :----:   | :----:   |:----:   | :----:   | ---:|
        | 29 333 517 | 27 481 394  | 28 038 666 | 27 083 573 | 23 196 570 | 24 892 581|
    
        Средний прирост в месяц:  ((28 038 666 - 27 481 394) + (24 892 581 - 23 196 570)) : 2 ~= 1 126 642<br>
        Средний прирост в день: 1 126 642 : 30 ~= 37 555<br>
        Регистируется каждый 10 пользователь, следовательно количество регистрацией в день: 3 756<br>
        Количество пользователей в день: 832 500, следовательно количество регистрацией в день на одного пользователя:<br>
        3 756 : 832 500 = 0.005
     

2) Рассмотрим усредненную пользовательскую модель действий в день:
    - авторизация - 1 раз
    - регистрация - 0.005 раз
    - Количество страниц за посещение - 6:
        - посещение главной страницы - 1 раз
        - посещение станицы категории - 2 раза
        - посещение станицы поиского запроса - 2 раза
        - посещение станицы мои объявления - 0.1 раза
        - посещение станицы мои заказы - 0.5 раза
        - посещение станицы кошелек - 0.1 раза
        - посещение станицы мои сообщения - 0.3 раза
    - отправка сообщений - 1
    - размещений - 0.25 раз
    

3) Оценка трафика
    - Авторизация ![auth](auth.png) Объем трафика ~ 173 КБ, количество запросов: 184<br><br>
    - Регистрация ![reg](reg.png) Объем трафика ~ 381 КБ, количество запросов: 144<br><br>
    - Главная страница ![get](get.png) Объем трафика для посещения страницы ~ 2.6 МБ, количество запросов: 72<br><br>
    - Страница категории ![cat](cat.png) Объем трафика для посещения страницы ~ 3.7 МБ, количество запросов: 381<br><br>
    - Страница поиского запроса ![sea](sea.png) Объем трафика для посещения страницы ~ 3.4 МБ, количество запросов: 325<br><br>
    - Страница мои объявления ![myy](myy.png) Объем трафика для посещения страницы ~ 907 КБ, количество запросов: 199<br><br>
    - Страница мои заказы ![ord](ord.png) Объем трафика для посещения страницы ~ 1.1 МБ, количество запросов: 241<br><br>
    - Страница кошелек ![cas](cas.png) Объем трафика для посещения страницы ~ 1.3 МБ, количество запросов: 294<br><br>
    - Страница мои сообщения ![mes](mes.png) Объем трафика для посещения страницы ~ 1.4 МБ, количество запросов: 366<br><br>
    - Отправка сообщения ![sen](sen.png) ![mes2](mes2.png) Объем трафика ~ 1 МБ, количество запросов: 1<br><br>
    - Отправка сообщения ![post](post.png) Объем трафика ~ 5 МБ, количество запросов: 1211<br><br>

4) Расчет трафика для посещения страниц одного пользовател в день
    - 173 КБ * 1 = 173 КБ, 184 * 1 = 184 запроса
    - 381 КБ * 0.005 = 1.91 КБ, 144 * 0.005 = 0.72 запроса
    - 2.6 МБ * 1 = 2.6 МБ, 72 * 1 = 72 запроса
    - 3.7 МБ * 2 = 7.4 МБ, 381 * 2 = 762 запроса
    - 3.4 МБ * 2 = 6.8 МБ, 325 * 2 = 650 запроса
    - 907 КБ * 0.1 = 91 КБ, 199 * 0.1 = 19.9 запроса
    - 1.1 МБ * 0.5 = 550 КБ, 241 * 0.5 = 120.5 запроса
    - 1.3 МБ * 0.1 = 130 КБ, 294 * 0.1 = 29.4 запроса
    - 1.4 МБ * 0.3 = 420 КБ, 366 * 0.3 = 109.8 запроса
    - 1 МБ * 1 = 1 МБ, 1 * 1 = 1 запроса
    - 5 МБ * 0.25 = 1.25 МБ, 1211 * 0.25 = 302.75 запроса
    - <b>Итого: 20.4 МБ, 2252 запроса</b>

5) Расчет дневного трафика
 - получаемый трафик<br>
   (2.6 МБ + 7.4 МБ + 6.8 МБ + 91 КБ + 550 КБ + 130 КБ + 420 КБ) * 832 500 = 15 313 171 500 КБ = 14.3 ТБ<br>
   72 + 762 + 650 + 19.9 + 120.5 + 29.4 + 109.8 = 1763.6 запроса
    
 - передаваемый трафик<br>
   (173 КБ + 1.91 КБ + 1 МБ + 1.25 МБ) * 832 500 = 2 063 692 575 КБ = 1.9 ТБ<br>
   184 + 0.72 + 1 + 302.75 = 488.47 запроса

6) Оценка пользовательской активности в день<br>
   Учитывая тот факт, что пользователи сервиса проживают в России, Германии, Великобритании.<br>
   Интервал часовых поясов:<br>
   ![map](map.png)
   Пользователи располагают от UTC+0:00 до UTC+12:00<br>
   Пользовательские часы начинаются с 09:00 по UTC+12:00, заканчиваются в 20:00 по UTC+0:00,<br>
   т. е. 32 - 9 часов = 23 часа

7) Оценка запросов в секунду<br>
   - GET: (1763.6 * 832 500) запросов : (23 * 3600) секунд = 17 732 запросов в секунду
   - POST: (488.47 * 832 500) запросов : (23 * 3600) секунд = 4 911 запросов в секунду
   
#### Итог по нагрузке:
- 14.3 ТБ получаемого трафика в день, 17 732 GET-запросов в секунду
- 1.9 ТБ передаваемого трафика в день, 4 911 POST-запросов в секунду

### Логическая схема БД
![logic](logic.jpg)

### Список источников:
1) <a href="https://www.similarweb.com/website/youla.ru/">similarweb, страница о Юле</a>
2) <a href="https://sitechecker.pro/app/main/traffic-checker-land?pageUrl=https:%2F%2Fyoula.ru%2F">sitechecker, страница о Юле</a>