<sup><sub>[Curriculum vitae in *english*: danil.kutkevich.ru][]</sub></sup>

# Данил Куткевич — бэкенд-разработчик

Привет!

Я Данил, пишу [бэк][go8583] на [Go][sqltee].
До 2016-го был [руби][rubycda].
Писал [финтех][Rocketbank1.0], [геймдев][Armor5Games] и [медтех][Medapp].

Привык к 100500 RPS, хочу столько же)

Работаю сам и в команде единомышленников

Рассчитываю на вознаграждение 300k рублей net.

Эл. почта <danil@kutkevich.org>  
Расположение Москва/Петербург  
Телефон +7 921 338 0130  
Гитхаб/[danil](https://github.com/danil)  
VK/[danilkutkevich](https://vk.com/danilkutkevich)

## Опыт

1. <span title="2023.11.27—2026.07.01">2023—2026</span>
   [Wildberries][wbtech.wildberries.ru]

   Файловое хранилище на Go, Kafka и Bare-metal, например:

   * Удаление директорий в географически-распределённом
     кластере <!-- в дополнение к удалению файлов,
     в хранилище 1го поколения c ручным сегментированием без мастера
     с [BGP][] и [Bird][] [1231011841][] -->

   * Разработка хранилища с шардированием
     нового поколения <!-- 2е покаление без ручного сегментирования
     c мастер-шлюзом -->

2. <span title="03.2021—08.2023">2021—2023</span>
   [ОЗОН банк][bank.ozon.ru]

   Банковское приложение на Go, PostgreSQL и K8s, например:

   * Сервис принимающий счета и отправляющий
     отчёты [311-П][]<!-- балансовые счетам второго порядка, например:
     40817 40820 40802 40701 40702 -->, а также отправляющий в ФНС ответы на
     запросы [440-П][]<sup><sub>[1][440-п цб]</sub></sup>

   * Система гарантирующая целостность передачи данных внутри банка,
     состоящая из шаблонизатора для Go generate и Protobuf контракта

3. <span title="08.2018—01.2021">2018—2021</span>
   [Рокетбанк][rocketbank.ru]

   * Банковский процессинг на Go, PostgreSQL, RabbitMQ, K8s — 120 RPS
     с гарантией ответа Мастеркарду/TSYS до 500 миллисекунд.
     Из интересного — кодек [ISO 8583][go8583], антифрод

   * Сервисы на Ruby on Rails: апи с Mastercard MDES<sup><sub>[4][mdes]</sub></sup>,
     платёжный шлюз c Точкой<sup><sub>[5][tochka]</sub></sup>

4. 07.2018—08.2018
   <span title="Xena.Exchange">Xena Exchange</span>

   Криптовалютная биржа на Go, PostgreSQL, RabbitMQ, K8s, например:

   * Проксирование финансовых отчетов из основного приложения в админку через
     foreign-data wrapper<sup><sub>[6][PostgreSQL foreign-data wrapper]</sub></sup> и
     Loopback3<sup><sub>[7][StrongLoop]</sub></sup>

   * Восстановление пароля и кэширование новостей для веб-приложения

5. <span title="10.2016—05.2018">2016—2018</span>
   [Armor5Games][]

   * Сервер мобильной игры [Rise of Pirates][] на Go, MySQL и MongoDB.
     Например приём платежей через Apple Store.
     120 RPS, 50k новых пользователей в неделю

   * Сервер мобильной игры Bing Han Garden на Go, PostgreSQL и MongoDB.
     Например RESTful API, приём платежей через Apple Store и Google Play.
     Готовился TCP сервер реального времени

6. <span title="06.2013—08.2016">2013—2016</span>
   [Waveaccess][waveaccess.ru]

   * Автоматизация сертификации [сверки терапии/лекарственных средств][rubycda]
     на Ruby on Rails и PostgreSQL. Система документооборота медицинского
     учреждения<sup><sub>[8][medapp]</sub></sup>,
     более 50-ти моделей <!-- [Clinical Document Architecture][CDA] -->

   * <span title="Holiadvice">Телемедицинская система</span>
     на Ruby on Rails и PostgreSQL. Например, приём платежей через Paypal,
     а также WebRTC-видеоконференция

   * Прототип <span title="Salemed">системы заказа магнитно-резонансной
     томографии</span> на Clojure и PostgreSQL

   * Система нагрузочного тестирования, запускаемая из CI на AWS для
     [Fhirbase][]/хранилище медицинских данных на основе PostgreSQL и FHIR

7. <span title="04.2012—06.2013">2012—2013</span>
   [Молинос][molinos.ru]

   * [НеваРеактив][nevareaktiv.ru] магазин химических реактивов
     на Ruby on Rails и MySQL. Из интересного — полнотекстовой поиск на Sphinx

   * Коллективный блог на Ruby on Rails и MySQL для [Оморфии][omorfia.ru] —
     постоянно действующего конкурса

8. <span title="09.2010—04.2012">2010—2012</span>
   OOO Аверс  
   Дописывал фриланс биржу на Ruby on Rails, MySQL,
   Sphinx поиск по адресам КЛАДР, генератор PDF налоговой декларации для ИП

9. <span title="03.2008—09.2010">2008—2010</span>
   [Джон студия][john.ru]  
   [Сайт хоккейного клуба СКА][ska.ru] на Ruby on Rails и PostgreSQL.
   Из интересного — настройка Nginx

10. <span title="11.2004—03.2008">2004—2008</span>
   [Дараут сервис][darout]  
   Переписал фронт
   <span title="hotelguide.com">бронирования гостиниц</span>
   с ColdFusion на JavaServer Faces

11. <span title="06.2003—11.2004">2003—2004</span>
   [Инвестиционная Компания Ленмонтажстрой][lmsic]  
   Мой первый проект — корпоративный сайт компании на PHP и MySQL

## Образование

[Санкт-Петербургский государственный университет телекоммуникаций им. проф. М.А.Бонч-Бруевича][bonch]
1997—2001  
Незаконченное высшее. Факультет многоканальных телекоммуникационных систем

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
