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

стр. 49
