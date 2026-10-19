<sup><sub>[Curriculum vitae in *english*: danil.kutkevich.ru][]</sub></sup>

# Данил Куткевич — бэкенд-разработчик

Привет!

Я Данил, пишу [бэк][go8583] на [Go][sqltee].
До 2016-го был [руби][rubycda].
Писал [финтех][Rocketbank1.0], [геймдев][Armor5Games] и [медтех][Medapp]
<!-- Работаю и самостоятельно, и в команде единомышленников -->
<!-- Привык к highload 10k+ RPS (чтение на каждом сервере) --><!-- https://en.wikipedia.org/wiki/C10k_problem -->
<!-- Рассчитываю на вознаграждение 450k рублей net -->

## Навыки

<sup><sub>Backend:</sub></sup> Go 9+ лет, Highload 10k+ RPS (чтение на каждом сервере)<!-- https://en.wikipedia.org/wiki/C10k_problem -->  
<sup><sub>Базы данных:</sub></sup> PostgreSQL, MySQL, ClickHouse, Redis, etcd  
<sup><sub>Инфраструктура:</sub></sup> Kafka, Linux, Bash, K8s, Ansible  
<sup><sub>Observability:</sub></sup> Prometheus, Grafana, OpenTelemetry  
<sup><sub>Практики:</sub></sup> <span title="High Availability">HA</span>, Микросервисы, CI/CD  
<sup><sub>Прочее:</sub></sup> <span title="gRPC/Protobuf">gRPC</span>, ISO 8583, <span title="Clinical Document Architecture">HL7 FHIR/CDA</span>  
<sup><sub>Английский язык:</sub></sup> технический, читаю документацию

## Контакты

Расположение Москва и Петербург (живу на два города, готов к офису с первого дня)  
Telegram&nbsp; [t.me/danilkutkevich](https://telegram.me/danilkutkevich)  
Эл.почта <danil@kutkevich.org>  
Телефон +7 921 338 0130  
VK/[danilkutkevich](https://vk.com/danilkutkevich)  
GitHub/[danil](https://github.com/danil)

## Опыт

1. <span title="2023.11.27—2026.07.01">2023—07.2026</span>
   [ВБ Тех][wbtech.wildberries.ru],
   старший бэкенд-разработчик

   * Дорабатывал высоконагруженное файловое хранилище (Go, Prometheus, Grafana)
     с ручным сегментированием
     (10k+ RPS чтения на каждом сервере, 5+ ДЦ, 100+ серверов bare-metal Linux).
     HA-архитектура спроектирована до меня: сегменты по артикулу
     зеркалируются между ДЦ, BGP anycast для failover, eventual consistency,
     запись через Kafka с LWW.
     Отказ узла или ДЦ не влияет на доступность;
     события, дошедшие до Kafka, не теряются.

     <!-- * HA-архитектуру спроектировали до меня. Отказоустойчивость обеспечивается:  
       — сегментирование по артикулу, сегмент зеркалирован между ДЦ,
         узлы равнозначные - единой точки отказа нет;  
       — запись файла принимается любым узлом,
         событие о нём публикуется в Kafka (реплицированный топик),
         подтверждение клиенту - после публикации,
         реплики подтягивают байты по HTTP;  
       — при конкурентной записи побеждает последняя версия
         по времени события (Last-Write-Wins), повторная доставка безвредна -
         повтор по времени всегда проигрывает;  
       — failover: узлы анонсируются по BGP anycast -
         при падении узла или целого ДЦ трафик уходит на живые реплики;  
       — чтение с eventual consistency
         (задержка репликации для сценариев клиентов допустима);  
       Результат: потеря узла или ДЦ не влияет на доступность;
                  данные, событие о которых дошло до Kafka,
                  не теряются при отказе узлов. -->

   * Реализовал удаление директорий в географически распределённом кластере
     — операция над множеством файлов стала практически мгновенной
     в восприятии пользователя <!-- в хранилище 1го поколения
     c ручным сегментированием без мастера с [BGP][] и [Bird][] [1231011841][] -->

   * Разрабатывал хранилище нового поколения
     без ручного сегментирования (ClickHouse, etcd) <!-- без ручного шардирования, 2е поколение
     c мастер-шлюзом -->

2. <span title="03.2021—08.2023">2021—2023</span>
   [Озон банк][bank.ozon.ru],
   ведущий бэкенд-разработчик

   Банковское приложение на Go и PostgreSQL
   (K8s, Prometheus, Grafana, OpenTelemetry, Jaeger),
   в том числе спроектировал:

    * Сервис налоговой отчётности (отправка в ФНС XML по [311-П][]
      на каждый счёт, <!-- балансовые счета второго порядка, в том числе:
      40817 40820 40802 40701 40702 --> ответ на
      запросы [440-П][]<sup><sub>[1][440-п цб]</sub></sup>).
      Нагрузка умеренная (~100 RPS), цена ошибки высокая
      (за ошибку в данных по каждому счёту штраф 30k+ рублей).
      Отказоустойчивость: БД и K8s в 3+ ДЦ,
      transactional outbox (at-least-once) + inbox (идемпотентный потребитель)
      = effectively-once.
      <!-- Отказоустойчивость обеспечивается:  
      — частичный отказ БД с автоматическим failover
        и реплицированной на 3+ ДЦ не останавливает сервис;  
      — отказ экземпляров сервиса компенсируется K8s (3+ ДЦ);  
      — сетевые сбои компенсируются повторами между сервисом
        и источником данных: transactional outbox + at-least-once доставка,
        потребитель идемпотентен (inbox) - итог effectively-once;  -->
      Результат: за 2+ года - отчётность по 1M+ счетам,
                 суммарный штраф < 100k рублей (единицы ошибок).

   * Система на основе шаблонизатора для Go generate и Protobuf-контракта,
     гарантирующая целостность передачи данных между микросервисами

3. <span title="08.2018—01.2021">2018—2021</span>
   [Рокетбанк][rocketbank.ru],
   старший бэкенд-разработчик

   * Банковский процессинг на Go, PostgreSQL, RabbitMQ, K8s
     — гарантия ответа Mastercard/TSYS до 500 миллисекунд.
     Из интересного — кодек [ISO 8583][go8583], антифрод

   * Сервисы на Ruby on Rails: API с Mastercard MDES<sup><sub>[2][mdes]</sub></sup>,
     платёжный шлюз с Точкой<sup><sub>[3][tochka]</sub></sup>

<!-- 4. 07.2018—08.2018
   <span title="Xena.Exchange">Xena Exchange</span>,
   старший бэкенд-разработчик

   Криптовалютная биржа на Go, PostgreSQL, RabbitMQ, K8s, в том числе:

   * Проксирование финансовых отчётов из основного приложения в админку через
     foreign-data wrapper<sup><sub>[4][PostgreSQL foreign-data wrapper]</sub></sup> и
     Loopback3<sup><sub>[5][StrongLoop]</sub></sup>

   * Восстановление пароля и кэширование новостей для веб-приложения -->

4. <span title="10.2016—05.2018">2016—2018</span>
   [Armor5Games][],
   старший бэкенд-разработчик

   * Сервер мобильной игры [Rise of Pirates][] на Go, MySQL, MongoDB и Ansible
     — 50k новых пользователей в неделю.
     В том числе приём платежей через App Store.

   * Сервер мобильной игры Bing Han Garden на Go, PostgreSQL и MongoDB.
     В том числе RESTful API, приём платежей через App Store и Google Play.
     <!-- Прототип TCP-сервера реального времени -->

5. <span title="06.2013—08.2016">2013—2016</span>
   [Waveaccess][waveaccess.ru],
   фулстек-разработчик

   * Автоматизация сертификации [сверки терапии/лекарственных средств][rubycda]
     на Ruby on Rails и PostgreSQL. Электронная медкарта
     (система документооборота медицинского учреждения<sup><sub>[4][medapp]</sub></sup>),
     более 50 моделей <!-- [Clinical Document Architecture][HL7 CDA] -->

   * <span title="Holiadvice">Телемедицинская система</span>
     на Ruby on Rails и PostgreSQL. В том числе приём платежей через PayPal,
     а также WebRTC-видеоконференция

   * Прототип <span title="Salemed">системы заказа магнитно-резонансной
     томографии</span> на Clojure и PostgreSQL

   * Система нагрузочного тестирования, запускаемая из CI на AWS для
     [Fhirbase][] (хранилище медицинских данных на основе PostgreSQL
     и FHIR) <!-- [Fast Healthcare Interoperability Resources][HL7 FHIR] -->

6. <span title="04.2012—06.2013">2012—2013</span>
   [Молинос][molinos.ru],
   бэкенд-разработчик

   * [НеваРеактив][nevareaktiv.ru] — магазин химических реактивов
     на Ruby on Rails и MySQL. Из интересного — полнотекстовый поиск на Sphinx

   * Коллективный блог на Ruby on Rails и MySQL для [Оморфии][omorfia.ru] —
     постоянно действующего конкурса

7. <span title="06.2003—04.2012">2003—2012</span>
   fullstack developer в стартапах и веб-студиях (Ruby on Rails, MySQL, Redis)  
   Более 5 успешно сданных проектов

<!-- 7. <span title="09.2010—04.2012">2010—2012</span>
   ООО «Аверс»,
   middle fullstack developer  
   Дописывал фриланс-биржу на Ruby on Rails, MySQL,
   Sphinx поиск по адресам КЛАДР, генератор PDF налоговой декларации для ИП -->

<!-- 8. <span title="03.2008—09.2010">2008—2010</span>
   [Джон студия][john.ru],
   middle бэкенд-разработчик  
   [Сайт хоккейного клуба СКА][ska.ru] на Ruby on Rails и PostgreSQL.
   Из интересного — настройка Nginx -->

<!-- 9. <span title="11.2004—03.2008">2004—2008</span>
   [Дараут сервис][darout],
   middle fullstack developer  
   Переписал фронт
   <span title="hotelguide.com">бронирования гостиниц</span>
   с ColdFusion на JavaServer Faces -->

<!-- 10. <span title="06.2003—11.2004">2003—2004</span>
   [Инвестиционная Компания Ленмонтажстрой][lmsic],
   middle fullstack developer  
   Мой первый проект — корпоративный сайт компании на PHP и MySQL -->

## Образование

Фундаментальное образование в
[Санкт-Петербургском государственном университете телекоммуникаций им. проф. М. А. Бонч-Бруевича][bonch]
1997—2001<!-- Неполное высшее. -->,
факультет многоканальных телекоммуникационных систем,
специальность "Банковские сети"
<!-- , после 3-го курса прошёл срочную службу в армии,
а с 2003 года непрерывно работаю в коммерческой разработке -->

<sub>[Curriculum vitae in *english*: danil.kutkevich.ru][]</sub>

[311-п]: https://nalog.gov.ru/rn77/about_fts/docs/8926082/
[440-п цб]: https://cbr.ru/development/feddc/fns
[440-п]: https://nalog.gov.ru/rn77/about_fts/interaction_other/bank_rf/
[armor5games]: https://armor5games.github.io
[bank.ozon.ru]: https://bank.ozon.ru
[bgp]: https://en.wikipedia.org/wiki/Border_Gateway_Protocol
[bird]: https://github.com/cz-nic/bird
[bonch]: https://sut.ru
[cda]: https://en.wikipedia.org/wiki/Clinical_Document_Architecture "CDA Clinical Document Architecture."
[curriculum vitae in *english*: danil.kutkevich.ru]: ./danilkutkevich.en.md#readme
[darout]: http://darout.ru
[fhirbase]: https://github.com/fhirbase/fhirbase-plv8/graphs/contributors?all=1
[go8583]: https://github.com/danil/iso8583
[john.ru]: https://john.ru
[lmsic]: https://lmsic.com
[strongloop]: https://github.com/strongloop "StrongLoop or LoopBack 3 and 2 (now LoopBack.io)."
[mdes]: https://developer.mastercard.com/mdes-customer-service/documentation
[medapp]: https://health-samurai.io
[molinos.ru]: https://molinos.ru
[nevareaktiv.ru]: https://nevareaktiv.ru
[omorfia.ru]: https://omorfia.ru
[postgresql foreign-data wrapper]: https://wiki.postgresql.org/wiki/Foreign_data_wrappers "PostgreSQL foreign-data wrapper."
[rise of pirates]: https://armor5games.github.io/ru/games/rise-of-pirates
[rocketbank.ru]: https://rocketbank.ru
[rocketbank1.0]: https://rocketbank.ru
[rubycda]: https://github.com/hospital-systems/ruby-cda
[ska.ru]: https://ska.ru
[sqltee]: https://github.com/danil/sqltee
[tochka]: https://tochka.com
[waveaccess.ru]: https://waveaccess.ru
[wbtech.wildberries.ru]: https://wbtech.wildberries.ru
[1231011841]: https://en.wikipedia.org/wiki/Bird_Internet_routing_daemon
