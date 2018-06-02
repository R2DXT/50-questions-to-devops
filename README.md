# 50-questions-to-ops
## Вопросы для DevOps инженеров и системных администраторов Unix
### 1. Как ты понимаешь концепцию: инфраструктура как код?
Подход «Инфраструктура как код (IaC)», который иногда называют «программируемой инфраструктурой», — это паттерн, по которому процесс создания/настройки инфраструктуры аналогичен процессу программирования ПО. По сути, этот паттерн положил начало устранению границ между написанием приложений и созданием сред для этих приложений. Это основа облачных вычислений и неотъемлемая часть DevOps методологии.
### 2. Как сохранить правило в iptables, чтобы после перезагрузки оно не затерлось?
Нужно ввести команду iptables-save.
### 3. Чтотакое inodes и что они хранят?
Это индексные дескрипторы — то есть структура данных в традиционных для UNIX файловых системах, таких как ext4. В этой структуре хранится метаинформация о стандартных файлах, каталогах или других объектах файловой системы, кроме непосредственно данных и имен файлов.
### 4. Что хранится в настройках sysctl? Какой командой можно применить новые настройки?
Это утилита, предназначенная для управления параметрами ядра операционной системы на лету. Позволяет читать и изменять параметры ядра. Например — такие, как размер сегмента разделяемой памяти, ограничение на число запущенных процессов и т.д.
Чтобы применить новые настройки нужно ввести команду sysctl –system.
### 5. Что такое RAID-массив? Какие бывают RAID-массивы? Назови основные отличия? Что такое диск чётности?
RAID (от англ. Redundant Array of Independent Disks — избыточный массив независимых дисков) — технология виртуализации данных, которая объединяет несколько дисков в логический диск для избыточности и повышения производительности при операциях чтения/записи данных.
     
RAID0 (stripe) — дисковый массив повышенной производительности с чередованием, без отказоустойчивости. Строго говоря, RAID-массивом не является, поскольку избыточность (redundancy) в нём отсутствует.

RAID1 (mirror) — зеркальный дисковый массив. Данные пишутся на 2 диска одновременно, то есть зеркально.

RAID2 — зарезервирован для массивов, которые применяют код Хемминга (Код Хемминга – это блочный код, позволяющий исправлять одиночные и фиксировать двойные ошибки).

RAID3/4 — дисковые массивы с чередованием и выделенным диском чётности.

RAID5 — дисковый массив с чередованием и отсутствием выделенного диска чётности.

RAID6 — дисковый массив с чередованием, использующий две контрольные суммы, вычисляемые двумя независимыми способами.

RAID10 — массив RAID0, построенный из массивов RAID1.

RAID01 — массив RAID1, построенный из массивов RAID0 (имеет низкую отказоустойчивость).

RAID50 — массив RAID0, построенный из массивов RAID5.

RAID05 — массив RAID5, построенный из массивов RAID0.

RAID60 — массив RAID0, построенный из массивов RAID6.

RAID06 — массив RAID6, построенный из массивов RAID0.

Диск чётности — это диск предназначенный для хранения контрольных сумм, вычисляемых при записи данных на RAID-массив.
### 6. Что такое xargs?
Это утилита для формирования списка аргументов и выполнения команды в UNIX‐подобных операционных системах. Команда xargs объединяет зафиксированный набор заданных в командной строке — начальных аргументов с аргументами, прочитанными со стандартного ввода, и выполняет указанную команду один или несколько раз.
 
### 7. Расскажи что такое LoadAverage(LA)?
В утилитах top, htop, atop эта метрика показывает среднее арифметическое значение загрузки ресурсов операционной системы относительно количества доступных процессорных (виртуальных) ядер по трём временным интервалам: 1 минута, 5 минут и 15 минут.
### 8. Что такое sed?
Stream EDitor — потоковый текстовый редактор, применяющий различные предопределённые текстовые преобразования к последовательному потоку текстовых данных. Часто применяется в однострочных консольных командах для редактирования данных “налету”.
### 9. Какой процесс имеет PID1 и за что он отвечает? В каких случаях этот процесс не является родителем всех процессов операционной системы?
Название процесса /sbin/init. Он отвечает за инициализацию ядра Linux.
В случае когда используется Docker-контейнер, процесс с PID1 внутри контейнера не тот же процесс /sbin/init который запустил ядро хост машины, а процесс Docker-демона который запустил контейнер.
### 10.Что такое pip и PyPI? Как они связаны между собой?
pip (от англ. Preferred Installer Program) — утилита управления пакетами (зависимостями), которые написаны на языке программирования Python.
PyPI (от англ. Python Package Index) каталог пакетов Python — написанных на языке программирования Python.
PyPI работает с системами управления пакетами pip и easy_install аналогичен PEAR для PHP и CPAN для Perl.
### 11.Что такое RVM?
RVM (от англ. Ruby Version Manage) — утилита для управления версиями в языке программирования Ruby. Позволяет в разных директориях (окружениях) использовать разные версии языка.    
### 12.Назови главное отличие между 2-ой и 3-ей версией Python?
Python2 изначально создавался только с поддержкой ASCII-символов. Самое главное изменение в Python3 — это нативная обработка символов Unicode. Что повлекло за собой другие изменения в архитектуре языка и ожидаемо оказало влияние на несовместимость 2-ой и 3-ей версий языка.
### 13.Назови различия между протоколами IPv4 и IPv6?
IPv4 использует 32 битное адресное пространство, которое имеет размер 4 байта. Это означает, что общее количество IP адресов в интернете может быть 232 степени, а это около 4,3 миллиарда.
В IPv6 адрес, размером 128 бит отличается от адреса IPv4. Каждая группа разделяется двоеточием вместо точки и состоит из 16 бит, в виде четырех шестнадцатеричных цифр. Первые 64 бита содержат информацию о сетевом адресе, которая используется для маршрутизации, остальные 64 бита содержат подробную информацию о сетевом интерфейсе хоста.
### 14.Что такое стек MEAN и в чём его особенность?
Стек MEAN состоит из технологий MongoDB, Express.js, Angular.js, Node.js.
Это пока единственный стек полностью написанный на одном языке программирования JavaScript (Официально его стандарт называется ECMAScript).
### 15.Что такое сетевой socket?
Это программный интерфейс для обеспечения обмена данными между процессами. Процессы при таком обмене могут исполняться как на одной ЭВМ, так и на различных ЭВМ, связанных между собой сетью. Сокет — абстрактный объект, представляющий конечную точку соединения.
### 16.В чём принципиальное отличие виртуальной машины от Docker- контейнера?
Виртуальная машина обладает собственным ядром, которое контролирует гипервизор, а Docker-контейнер использует ядро хост машины.
### 17.Какие системы оркестрации ты знаешь?
Ansible, Salt Stack, Chef, Puppet, CFEngine.
      
### 18.Что такое стек HashiCorp?
Это набор приложений для автоматизации управления жизненным циклом облачной инфраструктуры, выпускаемый компанией HashiCorp.
В набор входят: Terraform, Packer, Vagrant, Nomad, Consul, Vault.
### 19. Что такое Overlay network? В каких случаях этот режим работы может быть полезен и почему?
Overlay network — это общий случай логической сети, создаваемой поверх другой сети. Узлы оверлейной сети могут быть связаны либо физическим соединением, либо логическим, для которого в основной сети существуют один или несколько соответствующих маршрутов из физических соединений.
В случае использования AWS (Amazon Web Services) есть ограничение на количество маршрутов в таблице маршрутизации на инстансах AWS до 50 записей. При необходимости собрать кластер более чем из 51 инстанса необходимо использовать оверлейную сеть.
### 20.Что такое привилегированные порты и почему они так называются? Сколько всего портов на одном сетевом интерфейсе? Почему их столько?
Привилегированные порты составляют пул с 1-го по 1024-й. Привилегированными они называются, потому что для запуска приложения, желающего прослушивать такие порты требуются привилегии пользователя root.
На одном сетевом интерфейсе всего 65535 портов, то есть 216 степени.
Так устроен протокол TCP/IP на адресацию номеров портов отводится 16
бит (по 16 бит на отправителя и получателя).
### 21.Какие типы баз данных ты знаешь (например, реляционные, а ещё)?
Документо-ориентированные, графовые, столбцовые, файловые, а также хранилища ключей и значений.
### 22.Какие методологии ведения проектов разработки ПО ты знаешь?
KanBan, Scrum, Agile, Waterfall.   
### 23.Какие текстовые редакторы в Unix ты знаешь и умеешь использовать?
vi, vim, nano, ee (easy editor), emacs.
### 24.Что такое CIDR нотация? Сколько адресов в сетевой маске /29? Сколько хостов можно разместить используя такую маску и почему? Напиши маску сети /29 (по октетам).
CIDR — бесклассовая адресация (от англ. Classless Inter-Domain Routing). Метод IP-адресации, позволяющий гибко управлять пространством IP- адресов, не используя жёсткие рамки классовой адресации. Использование этого метода позволяет экономно использовать ограниченный ресурс IP-адресов, поскольку возможно применение различных масок подсетей к различным подсетям.
В сети с маской /29 — 8 адресов.
Разместить можно 6 хостов, потому что 2 адреса выполняют служебную функцию – 1-й становится адресом этой сети, последний используется для отправки пакетов на все доступные узлы сети.

Собеседник должен написать: 255.255.255.248. 
### 25.Что такое MapReduce? Как это работает?
MapReduce — это модель вычисления некоторых наборов распределенных задач с использованием большого количества компьютеров (называемых «нодами»), образующих кластер.

Работа MapReduce состоит из двух шагов: Map и Reduce, названных так по аналогии с одноименными функциями высшего порядка, map и reduce.

На Map-шаге происходит предварительная обработка входных данных. Для этого один из компьютеров (называемый главным узлом — master node) получает входные данные задачи, разделяет их на части и передает другим компьютерам (рабочим узлам — worker node) для предварительной обработки.

На Reduce-шаге происходит свёртка предварительно обработанных данных. Главный узел получает ответы от рабочих узлов и на их основе формирует результат — решение задачи, которая изначально формулировалась.    
### 26.Какие модели конкуренции и параллелизма ты знаешь?
Потоки выполнения и блокировки, разделение идентичности и состояния, акторы, взаимодействие последовательных процессов, лямбда- архитектура.
### 27.Назови основные отличия версий Linux: RHEL(Red Hat), CentOS, Debian, Ubuntu? Что такое LTS?
RHEL/CentOS используют систему RPM-пакетов, а Debian/Ubuntu используют систему DEB-пакетов.

Сборки RHEL/CentOS более консервативны к появлению новых технологических решений, используются исключительно проверенные временем версии программ и ядер Lunix. Новые версии выходят не чаще чем раз в 1-1,5 года.

Сборки Debian/Ubuntu более прогрессивны в плане появления новых версий пакетов. Таким образом на фоне RHEL/CentOS, Debian/Ubuntu выглядят более свежими решениями и позволяют использовать самые передовые разработки и технологии. Обновления выходят не реже 1 раза в 6 месяцев, особенно в Ubuntu Linux.

Релизы, помеченные как LTS (от англ. Long Term Support) дословно «поддержка в течение длительного периода» поддерживаются дольше, чем большинство релизов. До выпуска следующей версии LTS также периодически выпускаются обновления к текущей версии LTS, имеющие то же кодовое имя, но отличающиеся дополнительной цифрой после номера версии. Обновления для LTS релизов выпускаются в течении 5 лет с момента релиза.
### 28.Какие системы оркестрации Docker-контейнерами ты знаешь?
Swarm, Kubernetes, Nomad, Rancher.
### 29.Назови альтернативу Docker, как среде выполнения для контейнеров.
Rocket (rkt) — является альтернативой Docker, разработанной компанией CoreOS с прицелом на соответствие строгим требованиям к безопасности и производительности.
### 30.Что такое SELinux? Что такое AppArmor? В чём их отличия?
SELinux (от англ. Security-Enhanced Linux) — вспмагательная подсистема Linux созданная для улучшенния безопасности, реализаующая систему принудительного контроля доступа, которая может работать параллельно с классической избирательной системой контроля доступа.

AppArmor (от англ. Application Armor) — инструмент упреждающей защиты, основанный на политиках безопасности (известных также как профили от англ. profiles), которые определяют, к каким системным ресурсам и с какими привилегиями может получить доступ то или иное приложение. В AppArmor включён набор стандартных профилей, а также инструменты статического анализа и инструменты, основанные на обучении, позволяющие ускорить и упростить построение новых профилей.

В отличии от SELinux, AppArmor не использует расширенные атрибуты и не зависит от файловой системы. Доступ к ресурсам определяется на основе профилей (profiles), которые привязаны к пути файла или каталога, причем самого файла может и не быть на момент активации профиля. Профиль разрабатывается индивидуально под каждое приложение. Хотя в этом есть и недостаток: при переносе файла в SELinux за ним полностью сохраняется контекст безопасности. Также стоит отметить, что SELinux применяется в RHEL/CentOS, а AppArmor в Debian/Ubuntu.
### 31.В чем отличия применения параметра --add-host от директивы extra_hosts в контексте запуска Docker-контейнера? Что у них общего?
Параметр --add-host применяется при запуске контейнера с помощью CLI (Command Line Interface) однострочной командой, а директива extra_hosts применяется при описании конфигурации контейнера для его запуска с помощью Docker Compose или Docker Swarm.
Эти атрибуты делают одно и тоже, а именно добавляют запись в файл /etc/hosts внутри контейнера.
### 32.Что такое Helm?
Helm – это пакетный менеджер для запуска и управления приложениями в кластере Kubernetes. Helm позволяет выполнять ключевые операции по управлению приложениями, такие как установка, обновление или их удаление. Если совсем просто, то Helm можно легко рассматривать как yum в RHEL/CentOS или apt в Debian/Ubuntu.
Helm состоит из двух частей: Helm (клиент) и Tiller (сервер).   
### 33.Что такое Vagrant? Какими средами выполнения Vagrant может управлять?
Это консольная утилита для создания и управления виртуальными машинами и Doker-контейнерами.
Vagrant поддерживает технологии VirtualBox, Docker и lxc.
### 34.Какие виды виртуализации ты знаешь? Как они устроены внутри?
Паравиртуализация — техника виртуализации, при которой гостевые операционные системы подготавливаются для исполнения в виртуализированной среде, для чего их ядро незначительно модифицируется. Операционная система взаимодействует с программой гипервизора, который предоставляет ей гостевой API, вместо использования напрямую таких ресурсов, как таблица страниц памяти.
А также виртуализация на уровне операционной системы — которая позволяет запускать изолированные и безопасные виртуальные машины на одном хосте, но не позволяет запускать операционные системы с ядрами, отличными от типа ядра базовой операционной системы.
### 35.Какие стадии нагрузочного тестирования можно выделить, как ключевые?
Первая — количество запросов при котором начинается рост времени ответа тестируемого сервиса, вторая — количество запросов при котором наступает отказ в обслуживании (DoS), то есть перестаём отвечать вообще.
### 36.В чём отличия компилируемых, интерпретируемых и языков программирования смешанного типа?
1.Комплируемые языки
Работу компилируемых языков можно представить следующей схемой, жизненный цикл программы представляет собой следующие этапы:
• Написание исходного текста программы (source code).
• Компиляция в исполнимый файл (например .exe для Windows или
.dmg для macOS).
• Выполнение программы.
Такой подход обеспечивает высокое быстродействие. То есть программа готовится заранее, в тот момент когда она нужна, она просто запускается.
    
Примеры: Assembler, C, C++, Go.

2. Интерпретируемые языки
Соответственно, жизненный цикл программы сводится к:
• Написание. • Выполнение.
По сути интерпретируемые программы это так называемые "скрипты" - описание набора действий которые должен выполнить интерпретатор. То есть, интерпретатор это большая программа со множеством различных функций. А программа это указание какие функции в каком порядке вызвать, описанием взаимодействия этих функций.
Это специфические языки, например языки для создания веб-сайтов. 

Примеры: PHP, JavaScript, Python, Ruby.

3. Смешанного типа
Принцип работы языков смешанного типа (компилируемо- интерпретируемые) проиллюстрируем такой схемой:
Java относится именно к компилируемо-интерпретируемым языкам программирования. Интерпретатор в Java называется JVM (от англ. Java Virtual Machine).
Возникает вопрос, зачем такая сложность? Дело в том что такой подход объединяет преимущества компилируемых языков (скорость выполнения) и интерпретируемых (независимость от операционной системы и безопасность).

Примеры: Java, C#.
### 37.Назови плюсы и минусы — статической и динамической типизации?
Типизация — это свойство языка программирования различать типы данных. Например, целые числа, числа с двойной точностью (с плавающей запятой), строки и т.д.

Статическая типизация (static) вид типизации при котором переменная связывается с типом в момент объявления и не может изменить свой тип. Сложнее описывать, но труднее допустить ошибку.
 
Плюсы статической типизации:
• многие ошибки с типами можно обнаружить на этапе компиляции.
• исполнение языка со статической типизацией в большинстве случаев
быстрее нежели с динамической.

Минусы статической типизации:
• многословность, для некоторых задач чрезмерна излишняя, однако может компенсироваться средствами обобщенного программирования, как к примеру шаблоны (templates) в С++.

Динамическая типизация (dynamic) вид типизации при котором переменная связывается с типом в момент инициализации, а значит эта переменная в любой другой момент инициализации может изменить свой тип. Легче описывать, но проще сделать ошибку.

Плюсы динамической типизации:
• лаконичность, не надо указывать типы и следить за ними, особенно полезно, когда необходимо иметь переменную в которую будут записаны промежуточные данные.

Минусы динамической типизации:
• если откинуть грамотный стандарт оформления кода, то в ООП могут возникнуть трудности определения принадлежности к определенному классу.
• возможны сложности с автодополнением в IDE, особенно с классами, ибо что куда относится знает (возможно) только программист.
• динамическая типизация требует дополнительных внутренних действий для осуществления этого механизма, поэтому скорость исполнения такого кода, в большинстве случаев, будет ниже чем у статически типизированного кода.
### 38.В чём отличие протоколов TCP и UDP?
TCP — транспортный протокол передачи данных в сетях TCP/IP, предварительно устанавливающий соединение с сетью.
UDP — транспортный протокол, передающий сообщения-датаграммы без необходимости установки соединения.
 
Разница между протоколами TCP и UDP — в так называемой “гарантии доставки”.
• TCP требует отклика (подтверждения доставки) от клиента, которому доставлен пакет данных, и для этого ему необходимо установленное заранее соединение.
• Также протокол TCP считается надежным, тогда как UDP получил даже именование “протокол ненадежных датаграмм.
• TCP исключает потери данных, дублирование и перемешивание пакетов (искажение очерёдности), задержки. UDP все это допускает, и соединение для работы ему не требуется.
• Процессы, которым данные передаются по UDP, должны обходиться полученным, даже с потерями. TCP контролирует загруженность соединения, UDP не контролирует ничего, кроме целостности полученных датаграмм.
## 39.Объясни отличия в паттернах обработки объектов: LIFO и FIFO?
LIFO (Last Input First Output) — это стек, последним пришёл первым ушёл.
FIFO (First Input First Output) — это очередь, первым пришёл первым ушёл.
### 40.Какие виды доступа можно получить используя протокол SMB/CIFS или его открытую реализацию Samba?
Доступ на уровне ресурсов. Ограничения накладываются серверной стороной на каталоги общего доступа. Каждый сетевой каталог может быть защищен паролем и клиент должен указать этот пароль для получения доступа к файлам из общего каталога.

Доступ на уровне пользователей. Ограничения налагаются на каждый файл в каждом общем каталоге и они основаны на пользовательских правах. Каждый пользователь (клиент) должен войти на сервер под своей учетной записью и пройти аутентификацию. После завершения проверки подлинности клиент получает соответствующий идентификатор пользователя (user ID), который он должен предъявлять для получения доступа к ресурсам сервера.
### 41.Что такое Nmap?
Название Nmap — это сокращение от Network mapper. Это утилита для исследования (сканирования) сети и проверки безопасности.
   
### 42.Что такое Zombie процесс? При каких обстоятельствах процессу присваивается такой статус?
В Unix, дочерний процесс всегда выполняется под руководством своего родителя (процесса который его породил). Иными словами родительский процесс делегирует дочернему процессу часть инструкций для выполнения. Zombie — это процесс потерявший источник получения инструкций для выполнения, то есть своего родителя.

Zombie процесс появляется когда родительский процесс завершая свою работу не завершил свой дочерний процесс, который был порождён им ранее.
### 43.Что такое VXLAN?
VXLAN (Virtual Extensible LAN) — является технологией сетевой виртуализации, созданной для решения проблем масштабируемости в больших системах облачных вычислений. Она использует схожую с VLAN технику для MAC инкапсуляции Ethernet кадров (Layer 2) в UDP-пакеты, стандартно используется порт 4789.

VXLAN является развитием усилий по стандартизации на оверлейном протоколе инкапсуляции. Он увеличивает масштабируемость до 16 миллионов логических сетей и позволяет сетям 2 уровня одновременно сосуществовать по IP-сетям. При этом multicast или unicast (с Head-End Replication) используются для передачи широковещательного трафика.

Спецификация технологии VXLAN первоначально была создана компаниями VMware и Cisco.
### 44.Что такое TLS?
TLS (от англ. Transport Layer Security) — Протокол защиты транспортного уровня, как и его предшественник SSL (от англ. Secure Sockets Layer) — слой защищённых сокетов. Эти криптографические протоколы, обеспечиваюют защищённую передачу данных между узлами в сети Интернет.
### 45.Какие протоколы и методы авторизации поддерживает утилита curl?
cURL — Это утилита команднй строки включающая набор библиотек, в которых реализуются базовые возможности работы с URL страницами и передачи файлов.
    
cURL поддерживает работу с протоколами: FTP, FTPS, HTTP, HTTPS, TFTP, SCP, SFTP, Telnet, DICT, LDAP, а также POP3, IMAP и SMTP.

Методы аутентификации в cURL — базовая, дайджест, NTLM и Negotiate для HTTP, а также Kerberos для FTP.
Возможно возобновление передачи файла с места обрыва (при поддержке протоколом), туннелирование через HTTP-прокси, поддержка HTTP-Cookie.
### 46.Что такое Swap?
Это механизм виртуальной памяти, при котором часть данных из оперативной памяти (ОЗУ) перемещается на хранение на HDD (жёсткий диск) или SSD (твёрдотельный накопитель).
### 47.Что такое ORM?
ORM (от англ. Object-Relational Mapping) — объектно-реляционное отображение, или преобразование. Технология программирования, которая связывает базы данных с концепциями объектно-ориентированных языков программирования, создавая «виртуальную объектную базу данных».
### 48.Что такое Xen?
Xen — кроссплатформенный гипервизор, разработанный в Кембриджском университете и распространяемый на условиях лицензии GPL.
Основные особенности — поддержка режима паравиртуализации помимо аппаратной виртуализации, минимальность кода самого гипервизора за счёт выноса максимального количества компонентов за пределы гипервизора.
### 49.Что такое OSPF?
OSPF (от англ. Open Shortest Path First) — протокол динамической маршрутизации, основанный на технологии отслеживания состояния канала (link-state technology) и использующий для нахождения кратчайшего пути алгоритм Дейкстры.
### 50.С какой технологией ты познакомился вчера, на этой неделе, в этом месяце?
У собеседника должна быть эмоция, при ответе на этот вопрос.
     
