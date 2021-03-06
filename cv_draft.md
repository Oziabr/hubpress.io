# Твардовский Юрий, 1980
> Решатель, консультант, маг и телепат

## Навыки

- Понимаю что нужно бизнесу.
- Превращаю проблемы в задачи, расходы или не-проблемы.
- Нанимаю, обучаю, мотивирую, организую культуру, увольняю.
- Организую службы и процессы.

### Убер-навыки

- Супер-дешево и эффективно.
- Всё будет работать без меня.

## О себе

У меня накопился пакет скилов и улучшений для управления разработкой, который я хочу валидировать.
Проведя последние 12 лет в разработке понял, что каждый раз занимаюсь организацией процессов.
Чего от меня не ждут из позиции кодера, в результате у меня кпд низкий и работодатель не счастлив.
Поэтому хочу зайти и применить свои умения из менеджерской позиции, где есть потребность в моих скилах.

Всегда работаю на результат.
Это делает меня отличным приобретением там, где нужен рост, или нужно разобраться с уже случившимся ростом
(при неконтролируемом росте процессы превращаются в хаос и ресурсы начинают расходоваться неэффективно,
в этом месте нужно перенастраивать процессы чтобы не потерять вообще всё).
Но я не встраиваюсь в стабильные процессы: как только все улучшения выполнены, процессы отлажены,
исполнители наняты и обучены - мне больше нечем заниматься и я покидаю компанию.

Этим объясняется половина моих уходов, вторая половина вызвана неэтичным поведением руководства
(что слишком часто случается в русскоязычных коллективах, к сожалению).

## Опыт

### 2017
> **Провайдер услуг телемедицины** (Avizia)

  Работал над API между основной системой и мобильными приложениями
- Методологизация разработки

  До меня над этим участком работал один человек,
  и ему требовалось в конце каждого цикла (месяца) 2-3 дня чтобы собрать свои фичи в релиз.
  Но вместе со мной он стал тратить уже неделю на сборку всех наших фичь.
  Это был классический факап с git-flow, в норме все фичи складываются в релиз нажатием одной кнопки.
  
  Починил это собрав параллельные фичи в последовательные,
  а также линтером (криво расставленные скобки добавляли конфликтов при слияниях).
- починка CI

  До меня неакуратный коммит выливался на тестовый сервер и приводил его в нерабочее состояние
  (тестирование буксовало, головной офис не мог смотреть на нашь прогресс).
  
  Сделал так, что неакуратный коммит заваливающий наши внутренние тесты не выливался.
  Так же прорефакторил тесты.
- Ввод систем автодокументации и мониторинга изменений API

  Не ушло в тираж, к сожалению.
  Идея была в том, что бы перевести API-тесты на SWAGGER.
  Им же мониторить изменения API основного продукта (с разработчиками которого связь была очень плохая).
  Мониторить поведение нашего API (в котором было достаточно легаси, приводившего к дивным багам).
  И упразднить ручное документирование API (никогда не успевавшее за кодом, и съедавшее кучу времени у девов).
  
  Не ушло в тираж из-за бизнес модели нашего аутсорсера: он не понял как продавать больше времени,
  если мы перестанем заниматься разгребанием этой кривоты.

### 2015
> **Поддержка корпоративных продаж**
- Организация разработки системы управления продажами

  С моим приходом на проекте оказалось пять full-stack разработчиков, каждый пилил отдельный участок.
  Как обычно документацию никто не читал, код был организован у всех по разному
  (один кодер поставлял фронтенд с поломанной системой сборки,
  то есть никто кроме него не мог вносить в его фронтэнд изменения).
  И состоял из копипасты.
  Была, к примеру, эпичная задача, занявшая неделю-две (200-400 часов) всех разработчиков -
  поменять круглые кнопки (придуманные сбежавшим UIщиком) на стандартные бутстраповские.
  
  Оптимизация была достигнута путём внедрения стандартных компонентов шаблонизатора (jade mixins),
  и убеждения разработчиков в том, что мы прекращаям кодить копипастой (KPI для кодеров обкатывался тут).
- Создание группы QA (ручное+авто)
  
  PO (не по скраму, по бизнесу) почему-то был уверен (по бэклогу, конечно), что продукт готов на 90%.
  Он не замечал что дев, запиливая новую фичу, ломает старые (для дева это нормально - дев фокусируется на текущей задаче).
  
  У меня ушло 2-3 месяца на то, чтобы убедить PO открыть вакансии тестировщиков,
  потом ещё месяц чтобы нанять и обучить.
  В результате оказалось что проект надо чинить в неожиданных местах (и мы это сделали благодаря тестировщикам),
  А также что PO теперь может делегировать тестировщикам свои задачи (вбивка демо-данных, etc).

  Автоматическое тестирование я реализовал при помощи сценариев gherkin,
  что позволило пришедшему джуну описать весь функционал за два месяца
  (если интересно, я готов показать как это работает - это очень прикольная штука).
  
- Организация CI

  Перед тем как организовать тестирование, понадобилось внедрить git-flow и развернуть CI
  (переехать с внутреннего гитлаба на гитхаб [из-за медленных несговорчивых внешних админов первого],
  развернуть striderCI [сейчас больше сервисов, и travis лучший]).
  Чтобы тестировщики могли принимать фичи от девов (одна фича - один тестовый сервер).
  И куда более сложная задача: консолидировать изменение базы
  (пять fullstack девов, если помните, каждый не стесняется менять базу).

  Консолидация базы была сделана путём выгрузки схемы (postgreSQL) в git при помощи CI,
  и нескольких самописных скриптов для проверок перед слиянием.
### 2013
> **Интернет-магазин** (AMF)
- Восстановление системы публикации маркетинговой информации, обучение контент-менеджера

  После того как из-за странного поведения управленцев разбежались все синьёры,
  оставшиеся мидлы захватили власть в дурдоме и захардкодили всё везде.
  В результате простая задача по публикации странички на сайте стала занимать неделю работы этих двух мидлов.
  
  Убрав хардкод и наняв студента (обучил его азам контент-менеджмента) удалось свести эту же задачу к 2-3 часам работы студента.
- Обновление системы заказов
  
  Мидлы наваяли одностраничную корзину заказов, обосновав её очень странными метриками
  (время, потраченное клиентом на работу с корзиной, без учёта брошеных корзин).

  Мы отрыли в коде старую корзину, с функционалом удовлетворяющим требованиям отдела маркетинга, и перезапустили её.
### 2011г
> **другой Региональный Интернет Провайдер** (Би-лайн)
- Разработка единой системы учёта ресурсов для группы компаний
  
  Интеграцию делали другие люди, на меня легла задача реализации контроля доступа в системе.
  На удивление, эта задача приходила ко мне не меньше четырёх раз, и для неё нет стандартов и эталонных реализаций
  (всё что я видел внутри фреймворков не тянет реальные ситуации и требует допиливания, но чаще замены).

  Сейчас я, наверное, знаю очень много об управлении доступом )
  Моё решение для билайна было принято, но я не отслеживал его судьбу.
### 2010г
> **Банк** (ТКС)
- Разработка и запуск конструктора форм для отдела кредитования

  Упражнение на тему "как сделать гибкий, конфигурируемый продукт" и "как передать управление логикой непрограммистам".
  Сделал из шаблонизатора smarty (он утратил актуальность, сейчас jade лучший),
  конструктор позволял собирать многостраничную форму просто называя ярлыки и типы полей в конфиге.
- Интеграция адресного каталога
  
  Российский КЛАДР - очень суровая штука.
  Мне нужно было на его базе сотворить поле формы для ввода адреса.
  Чтобы пользователь не сломал об него пальцы, я сделал ранжирование результатов поиска секциями
  по типу населённых пунктов и по типу совпадений.
- Отказ работать с Backbase 2.0
  
  Меня взяли на этот проект из-за указанного в резюме backbase
  (ничего общего не имеющего с 2.0, то был набор компонентов для фронта - идеологический предок angularjs).
  2.0 был сваян из дотнетовского конструктора форм,
  обрезанной джавы в качестве вебсервера,
  и файлопомойки alfresco.
  Ничего из перечисленного нормально не работало:
  конструктор не умел криптографию, и позволял любому нажавшему F12 почитать все недозаполненные формы
  (а кредитные формы - это вся возможная личная информация, плюс собственность);
  вебсервер на каждого нового посетителя генерировал сессию по 15-30 секунд
  (пользователь был вынужден сосерцать белую страницу всё это время);
  файлопомойка - сама её идея довольно дурацкая (здоровые люди хранят документы в CRM или ERP)
  и поставлялась она на отъеб%сь.
  В добавок взаимодействия с разработчиками практически небыло, проблемы не решались.
  
  Спустя 2-3 года на очередном собеседовании я столкнулся с пацанами, которые это несчастье закапывали в 2011ом.
  Как я понял, большинство проблем остались нерешенными.
  
### 2007г
> **Региональный Интернет Провайдер** (РТКомм)
- Разработка и внедрение ERP: трекинг задачь и ресурсов, мониторинг

  Тут было много инженерной работы по реверс-инжинирингу и поддержке старых систем, и переезду на новые.
  
  Из интересного мы сотворили мониторинг, складывавший по 5 миллионов записей в базу ежедневно.
  При помощи DBA, полки с дисками и постгресовых (или оракловых) партиций.
  Это был hi-load за долго до того, как он стал трендом.

### 2005г
> **Интернет Провайдер**

  Здесь я вырос за три года из техника-подключателя до CTO.
  Потому что были проблемы, которыми больше никто не желал заниматься.
- Запуск биллинговой системы взамен нерабочей, доработка её под бизнес
  
  Первая биллинговая система была сконструированна таким образом,
  что бы каждые пять минут пересчитывать всю историю всех пользователей за всё время её работы.
  Предсказуемо, никакой апгрейд сервера не мог удовлетворить возрастающую сложность вычислений.
  В результате серверных ресурсов стало нехватать и сервер перестал исполнять другие задачи
  (например, записывать сессии клиентов).
  
  Быстро проведя анализ рынка продуктов остановился на lanbilling (которые ещё и сидели в соседнем районе) -
  качественном продукте с открытым веб-интерфейсом.
  Развернул (работая на том же объёме нагрузка на сервер не превышала 10%, всё работало как часы).
  После чего допиливал интерфейс что бы не тратить по пять кликов на одно простое действие и удобно было искать
  (сейчас это стандартная сортируемая табличка с кнопочками, но тогда это было откровением).
- Проектирование и развитие сети

  Было много хардкора, в результате у нас работала сеть теоретически не возможная, мы поддерживали её опытом.
  Работала, естественно, далеко не идеально )
  Пока не пришли новые технологии (оптоволокно, управляемые свичи, etc).
- Методологизация работы монтажной службы

  Обычная инженерная работа: как кинуть провод между крышами, обжать, скрутить, подписать шнурок, подвести электричество.
- Запуск коммерческой службы поддержки

  Личный проект.
  Работая с последней милей обнаружил у клиентов запрос на помощь в повседневных задачах,
  восстановлении виндусов, борьбе с малварью.
  Нанял пацанов, дал им простые методички и отпустил работать.
  
  Большого коммерческого успеха не получилось, но всем было хорошо:
  клиенты могли работать, компания - продавать интернет услуги.
## Прочее (для консультирования, обучения, супервайзинга)
- эксперт в веб-разработке (фуллстэк, предпочитаю JS/CS)
- понимаю UI/UX и дзен-дизайн (фокус на контенте)
- архитектор/администратор баз данных (предпочитаю postgresql)
- администратор UNIX и сетей передачи данных
- архитектор без-серверных систем

### самопровозглашенный
- software archaeologist - знаю старые методы, позволяющие производить софт дешево и результативно
- software exorcist - умею заменить 15 синьёров на пяток стажеров под руководством одного синьёра, повысив результативность на порядок

## личное
- нетерпим к мудачеству
- обожаю делать полезные, работоспособные и автономные штуки
- хочу мир во всём мире, разумных роботов и освоения дальнего космоса
