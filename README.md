# Создание микросервисов - Сэм Ньюмен

## Микросервисы — это небольшие, автономные, совместно работающие сервисы.
### Небольшие и нацеленные на то, чтобы хорошо справляться только с одной работой
* Single Responsibility Principle, которое гласит: «Собирайте вместе все, что изменяется по одной и той же причине, и разделяйте все, что изменяется по разным причинам».
*  Микросервисы - код, который может быть переписан за две недели.
* Если для управления небольшой командой база программного кода слишком велика, весьма разумно будет изыскать возможности ее разбиения на части.
### Автономные
* Наш микросервис является самостоятельным образованием, которое может быть развернуто в качестве обособленного сервиса на платформе, предоставляемой в качестве услуги, — Platform as a Service (PAAS)
* Мы стараемся не заполнять несколькими сервисами одну и ту же машину
* **Обмен данными между самими сервисами ведется через сетевые вызовы, чтобы упрочить обособленность сервисов и избежать рисков, сопряженных с тесными связями.**
* Этим сервисам необходимо иметь возможность изменяться независимо друг от друга и развертываться, не требуя никаких изменений от потребителей
*  Если объем совместно используемого будет слишком велик, потребляемые сервисы станут завязываться на внутренние представления. Это снизит автономность, поскольку при внесении изменений потребует дополнительного согласования с потребителями. 
* **Наши сервисы выставляют напоказ программный интерфейс приложения — Application Programming Interface (API), и работающие на нас сервисы связываются с нами через эти API.**
* Это может означать выбор API, нейтральных по отношению к тем или иным технологиям, чтобы гарантировать отсутствие ограничений в выборе технологий
### Технологическая разнородность 
* Имея систему, составленную из нескольких совместно работающих сервисов, можно прийти к решению использовать внутри каждого из них различные технологии. Это позволит выбрать для каждого задания наиболее подходящий инструментарий, не выискивая какой-либо стандартный подход на все случаи жизни, зачастую заканчивающийся выбором наименьшего общего знаменателя. 
* Микросервисы также позволяют быстрее внедрять технологии и разбираться в том, чем именно нововведения могут нам помочь. 
### Устойчивость
* ***Ключевым понятием в технике устойчивости является перегородка.*** При отказе одного компонента системы, не вызывающем череду связанных с ним отказов, проблему можно изолировать, сохранив работоспособность всей остальной системы. 
***Именно такими перегородками для вас станут границы сервисов.***
### Масштабирование
* При работе с небольшими сервисами можно расширить только те из них, которые в этом нуждаются, что позволяет запускать другие части системы на небольшом, менее мощном оборудовании
### Простота развертывания 
* При использовании микросервисов можно вносить изменения в отдельный микросервис и развертывать его независимо от остальной системы. Это позволит развертывать код быстрее. 
* Возникшую проблему можно быстро изолировать в рамках отдельного сервиса, упрощая тем самым быстрый откат. 
* Это также означает, что новые функциональные возможности могут дойти до клиента быстрее. 
### Решение организационных вопросов 
* Также общеизвестно, что небольшие команды, работающие с небольшим объемом исходного кода, как правило, показывают более высокую продуктивность. 
### Компонуемость
* Применение микросервисов позволяет пользоваться какой-либо функциональной возможностью различными способами и для достижения различных целей. 
* Теперь следует думать обо всех многочисленных способах, которые нужны для построения хитросплетений всех возможностей для веб-приложений, простых приложений, мобильных веб-приложений, приложений для планшетных компьютеров или переносных устройств.
* При работе с микросервисами нужно думать о том, что мы открываем стыки, адресуемые внешним частям.
### Оптимизация с целью последующей замены
### А как насчет сервис-ориентированной архитектуры?
* Сервис-ориентированная архитектура (Service-oriented Architecture (SOA)) представляет собой подход в проектировании, при котором несколько сервисов работают совместно для предоставления некоего конечного набора возможностей

## Архитектор развития 
### Неверные сравнения
* Архитектор ПО - это скорее градостроитель
### Зонирование
* Зоны - границы сервисов или, возможно, собранных в крупные модули групп сервисов. В качестве архитекторов нам нужно больше заботиться не о том, что происходит внутри зоны, а о том, что происходит между зонами. То есть нужно тратить время на обдумывание вопросов общения сервисов друг с другом или того, как можно будет обеспечить подходящее отслеживание общей жизнеспособности системы. 
* ***Лучше стандартизировать, чтобы все мервисы использовали ограниченное количество технологий***

## Принципиальный подход 
* Стратегические цели - Принципы (не более 10) - Инструкции (Способы соблюдения принципов)
* Пример, как это реализуется:
* Должна быть стандартизация в компании и на уровне команд, как они будут реализовывать взаимоденйствие для своих сервисов.
* Нужен мониторинг отслеживания работоспособности нод. Для метрибыть Graphite, а для отслеживания работоспособности — Nagios.
* *Если, к примеру, выбор пал на HTTP/REST, что вы будете использовать, глаголы или существительные? Как станете работать со страничной организацией ресурсов? Как будете справляться с управлением версиями конечных точек?*

## (Control Objectives for Information and Related Technology (COBIT)): 
«Руководство обеспечивает уверенность в достижении целей предприятия путем сбалансированной оценки потребностей заинтересованных сторон, существующих условий и возможных вариантов, установления направления развития через приоритизацию
и принятие решений, постоянного мониторинга соответствия фактической продуктивности и степени выполнения требований установленным направлению и целям предприятия».

## Как моделировать сервисы
При проектировании микросервиса надо учитывать ***слабую связанность*** и ***сильное зацепление***

### Слабая связанность 
* Когда между сервисами наблюдается слабая связанность, изменения, вносимые в один сервис, не требуют изменений в другом. Для микросервиса самое главное — возможность внесения изменений в один сервис и его развертывания без необходимости вносить изменения в любую другую часть системы.
### Сильное зацепление 
* Хотелось бы, чтобы связанное поведение находилось в одном месте, а несвязанное родственное поведение — где-нибудь в другом.

### Ограниченный контекст
* конкретная ответственность, обеспечиваемая четко обозначенными границами
## Общие и скрытые модели 
Между сервисами должны ходить только общие модели, а внутренние должны быть скрыты.
***картинка 2***
***микросервисы нужно четко вписывать в ограниченные контексты.***
С обретением достаточного опыта вы можете решиться пропустить этап моделирования ограниченного контекста в виде модулей в составе более монолитной системы и сразу перейти к отдельному сервису. Но на начальном этапе нужно сохранять монолитность новой системы. Неверное определение границ сервиса может обойтись довольно дорого, поэтому нужно дождаться стабилизации представлений, чтобы справиться с новой областью более разумно
### Преждевременная декомпозиция 
Преждевременная декомпозиция системы на микросервисы может обойтись весьма дорого, особенно если область вам плохо известна. Во многих отношениях куда проще иметь весь исходный код, требующий декомпозиции и разбиения на микросервисы, чем пытаться создавать микросервисы с самого начала.
### Бизнес-возможности
Приступая к обдумыванию ограниченных контекстов, имеющихся в вашей организации, нужно размышлять не в понятиях совместно используемых данных, а в понятиях возможностей, предоставляемых такими контекстами всей остальной области. 
Поэтому сначала нужно задать себе вопрос «Чем этот контекст занимается?», а затем уже вопрос «А какие данные ему для этого нужны?». 
### Обмен данными с точки зрения  бизнес-концепций
Важно также продумать обмен данными между этими микросервисами с точки зрения одних и тех же бизнес-концепций. Моделирование программного продукта относительно вашей области бизнеса не должно останавливаться на замысле ограниченных контекстов. Одинаковые понятия и идеи, совместно используемые отделами вашей организации, должны быть отображены в интерфейсах. 

# Интеграция
* Нужно избегать любых технологий, вынуждающих нас выставлять напоказ внутренние представления деталей сервисов.
## Архитектурные подходы
### Совместно используемая база данных
Это когда несколько кодовых баз, завязаны на одной базе.
Фактически база данных представляет собой слишком большой совместно используемый API, который к тому же весьма хрупок.
Сильное зацепление и слабая связанность. А с интеграцией при помощи базы данных мы теряем и то и другое.
### Синхронные и асинхронные принципы
При синхронном обмене данными делается вызов на удаленный сервер, блокирующий всю работу вплоть до завершения операции. При асинхронном обмене данными вызывающая сторона перед тем, как вернуть управление, не будет дожидаться завершения операции и даже может не беспокоиться о ее завершении.

«запрос — ответ» или «опора на события».
При применении стиля «запрос — ответ» клиент инициирует запрос и ждет получения ответа. Эта модель полностью вписывается в синхронный обмен данными,но может работать и при асинхронном обмене. Можно начать операцию и зарегистрировать обратный вызов, обращаясь к серверу с просьбой дать знать о том, когда операция будет завершена.

Оркестрового принципа за основу берется центральный интеллект, направляющий процессы и управляющий ими, во многом напоминающий своими действиями дирижера оркестра. 
При использовании хореографического принципа каждую часть системы информируют о поставленной перед ней задаче, а детали разрешается прорабатывать самостоятельно, они подобны танцорам, находящим собственный путь и реагирующим на всех окружающих их артистов балета.

Оркестровый подход       - риск создания божственных сервисов. Такая архитектура может оказаться хрупкой и требовать больше изменений.
Хореографический принцип - разобщенно, сервисы подписывабтся на события. Более гибкие и разобщенные, но требуют отслеживания.

Для связывания микросервисов используют RPC и REST API.
Автор за использование http - FULL REST API - XML (JSON выбирает большинство) - *будем счиатать это каноном*

Автор за использования асинхронные сервисов с подпиской - и их дальнейшим контролем - *будем счиатать это каноном*

Общая кодовая база это лишняя связность кода, лучше его дублировать для микросервисов.

Нельзя выносить много логики в клиентскую библиотеку. В идеале только вызовы. 
SDK лучше, чем библиотека, так как не привязывает к определенной технологии.

Когда происходит событие, нужно запрашивать актуальную информацию о сущности. Это эффективно делать по ссылке, в момент выполнения события.

*Семантическое управление* - MAJOR.MINOR.PATCH (ВАЖНЫЙ.ВТОРОСТЕПЕННЫЙ.ИСПРАВЛЕНИЕ). MAJOR - нет обратной совместимости. MINOR - добавление функциональности, не ломает совместимость. PATCH - фикс багов


### Управление версиями
* В одном сервисе может сосуществовать старая и новая версия api. Это дает время клиентам перекунуть функциональность.
* В один момент существует старая и новая версия сервиса. Но прикрепленные к одной версии БД. (Автор не приветствует такой подход)
* 

стр. 97
