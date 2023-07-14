https://www.youtube.com/watch?v=glNn6yFyl5U

Automate dependency updates with Renovate Building a microservices-based NodeJS and React app
Всем привет! Это видео является частью серии видеороликов, в которых мы разрабатываем приложение для социальных сетей на базе микросервисов. Мы используем react для нашего интерфейса и узла. А также node.js для наших внутренних сервисов. Но вы также можете посмотреть это видео как отдельное видео, если вы заинтересованы в автоматизации зависимостей нашего проекта.
Мы начнем с обсуждения того, почему автоматизация управления зависимостей необходима даже для небольших проектов. Затем мы перейдем к изучению возможных решений и внедрим одно из них в наш проект.
Итак, вот наша повестка дня на сегодняшний день. Мы начнем с обсуждения того, зачем нам нужно автоматизированное управление зависимостями.
Затем мы обсудим одно из возможных решений, обновлений системы. Мы настроим ее на весь проект в целом, который будет включать в себя три этапа. Во-первых, нам нужно добавить Remote. Это файл в формате json.
Затем мы настроим базовую ветвь на обновление зависимостей. И я вернусь к этому позже, чтобы объяснить, почему я принял такое решение.
А потом мы настроим ее на автоматическое слияние. Мы также вернемся к этому вопросу позже, когда приступим к настройке. Я объясню, что представляет собой автоматическое слияние и как оно может быть нам полезно.
Затем мы проверим и объединим некоторые запросы на первое вытягивание из программы Renovate.
Итак, я вернулся к своей среде разработке ide. Мы видим, что в нашем пакете уже есть довольно много зависимостей. Это json-файл, предназначенный только для микросервиса аутоинтефикации. Теперь это только производственные зависимости. Есть также зависимости от разработки.
Если я добавлю цифры сейчас, они составят около 30 зависимостей, которыми нам нужно будет управлять вручную, если мы захотим обновить их, не имея решения автоматического управления. Это не подается масштабированию. Это отнимает много времени поддерживать все зависимости в актуальном состоянии. И речь идет только о микросервисе аутентификации.
Позже мы также добавим веб-клиент, добавим другие микросервисы и будем поддерживать все эти зависимости в актуальном состоянии. И на все это у нас нет времени.
Даже если мы были бы крупной компанией, имеющей большими ресурсами, это все равно было бы потрачено впустую, потому что оно может быть автоматизировано с помощью инструментов, которые уже существуют.
В чем заключается главная причина, по которой нам нужны автоматизированные зависимости? Конечно, есть и другие преимущества. Например, обновление для системы безопасности стоит очень дорого. Они применяются гораздо быстрее, чем, если бы мы постоянно отслеживали пакеты обновления для системы безопасности. Так что я почти уверен, что нет ни одного аргумента, который бы говорил: «Хорошо, нам не следует использовать автоматизированные решения для управления зависимостями».
Надеюсь, это дает краткое представление о том, зачем нам это нужно в нашем проекте.
Давайте перейдем к обсуждению, что представляет собой Renovate. Я могу упомянуть и другие решения, поддерживаемые GitHub, но здесь я решил использовать Renovate. И позже в этом видео я объясню, почему это так.
Итак, я нахожусь на домашней странице компании Renovate. Она предоставлена компанией WhiteSource и является бесплатной, так что мы можем просто установить ее в качестве приложения на GitHub в наш репозиторий GitHub. Мы также можем скачать ее бесплатно. Если вы хотите запустить инструмент обновления их командной строки, это может быть одно приложение. Еще одно приложение можно использовать, если вы хотите настроить его локально. Но здесь мы будем использовать приложение GitHub.
И это приложение GitHub позаботиться о мониторинге нашего репозитория GitHub. И создание запросов на извлечение всякий раз, когда появляются обновления для любого из наших пакетов. Все в порядке.
Как нам установить  это приложение? Давайте зайдем на GitHub, но прежде позвольте мне упомянуть об одной из возможных альтернатив Renovate. Это Dependabot. Это еще один автоматизированный инструмент управления зависимостями. Если вы не хотите использовать программу Renovate по каким-то личным причинам или уже пользуетесь Dependabot в другом месте, то вы можете им воспользоваться.
На мой взгляд, Dependabot с новой версией, которая поддерживается в GitHub, произошел большой облом. И проблема в том, что она не поддерживает автоматическое слияние. Это и может по-настоящему раздражать.
Представьте себе, что у нас есть 5 микросервисов и, возможно, в будущем каждый микросервис будет содержать список из 60-ти зависимостей. А, может быть, и 5060 зависимостей. И у нас огромный список PR-сервисов, которые необходимо просмотреть вручную. По-моему, это ни к чему хорошему не приведет.
Мы можем имитировать поведение автоматического слияния с другими действиями на GitHub. Но тогда нам нужно добавить больше настроек, чем есть на самом деле. Это необходимо в нашем хранилище. Я так и сделаю. Я не очень доволен таким решением с их стороны. Может быть, позже они представят эту конфигурацию, и мы сможем перейти на Dependabot.
Если вы хотите использовать более старую версию Dependabot, то это тоже возможно. Так что вы еще можете использовать 1-ую версию. И там они поддерживают функцию автоматического объединения, но уже довольно настойчиво настаивают на том, чтобы изначально перейти на GitHub. Именно по этой причине я решил использовать программу Renovate.
Если в будущем произойдут эти изменения, то, возможно, мы могли бы рассмотреть возможность перехода на Dependabot. Честно говоря, мне нравится тот факт, что у Dependabot более простой конфигурационный файл.
Если мы посмотрим на обновление, позвольте мне просто переключить вкладки. Здесь есть много возможностей для настройки. Это хорошо. Это подходит практически для любого сценария использования. И это может быть ошеломляющим.
В нашем случае мы будем использовать несколько конфигураций, которые предусмотрены нашими опциями конфигурации, предоставляемые компанией Renovate.
Мы не собираемся слишком много набрасывать или вдаваться в подробности, но я бы предпочел, чтобы конфигурация была несколько проще для работы. Именно по этой причине я бы предпочел использовать Dependabot. Но поскольку в Dependabot нет автоматизированных зависимостей, нет автоматического объединения, то это действительно главная для меня причина не использовать его.
Итак, я нахожусь на своей странице настроек. И теперь я хочу показать вам, как можно установить или проверить установку белого исходного кода в проекте.
Если вы находитесь на этой странице, вы можете нажать на кнопку «Установить бесплатно». После этого вы попадете на соответствующую страницу GitHub, где установите обновление своего проекта. Но если вы захотите позже проверить правильность установки или настроить ее, вам нужно зайти на страницу настроек. Внизу есть приложение.
Как только мы нажмем на кнопку «Приложение», мы увидим, что там есть список приложений. У меня установлено еще два других приложения. Но здесь есть предложение обновить приложение. И как только я нажму на кнопку «Настроить», у меня появится список или все, что связано с обновлением приложения.
Так что есть возможность скопировать и вставить базовый конфигурационный файл. Нам нужно будет изменить здесь несколько вещей, потому что это угловая программа. На самом деле это не имеет отношение к нашим целям.
Если я зайду еще глубже, то мы увидим, что у нас есть пара обновлений разрешений. Может быть, у вас этого нет, потому что вы уже установили программу обновления, и вам уже предоставили последнюю версию разрешений. Я могу сделать это позже. Это не проблема.
А затем в разделе «Выбранные хранилища» я могу выбрать хранилище, к которому я хочу предоставить доступ. Сейчас у меня есть здесь еще несколько других хранилищ. Но это всего лишь небольшие личные проекты, не представляющие интереса для данного видео. Самое главное, чтобы я выбрал не социальное приложение, а затем нажал кнопку «Сохранить».
Вскоре после сохранения новой конфигурации приложения Renovate и добавления репозитория, у нас появилась информация, которую нам нужно  объединить, чтобы активировать обновление.
Если вы хотите ознакомиться с текстом этой информации, то не стесняйтесь. В ней точно описано, как будет работать программа Renovate в хранилище.
Мы просто пройдемся по этому вопросу и объединим эти данные. А затем приступим к более тщательной работе с конфигурацией программы Renovate.
Я объединил данные по связям с общественностью.
Давайте вернемся к терминалу и установим последнюю версию Мастер. А затем скорректируем конфигурацию программы Renovate.
Я снова сижу за своим терминалом. Давайте возьмем последнюю версию программы Мастер и создадим новый запрос на извлечение или новую ветвь.
Давайте посмотрим, что это будет за обновление. Назовем это примерно так. И я уже могу нажать на эту кнопку, чтобы просто установить ветку вверх по течению вот так.
А сейчас мы перейдем к идентификатору и продолжим работу с конфигурацией. Как вы можете видеть здесь, он состоит из пяти строк кода и просто гласит, расширяет базовую конфигурацию.
Что означает эта базовая конфигурация? Какие именно опции здесь включены или отключены. Если мы просто погуглим это, то сможем перейти на страницу, где будет представлен более подробный список того, как параметры реализованы в базовой конфигурации.
Для нас здесь так важно, чтобы автоматическое объединение было отключено. Так что это именно то, что мы хотим изменить.
Давайте вернемся в репозиторий и посмотрим – есть ли уже какие-то открытые запросы на извлечение данных от Renovate. Один запрос на извлечение уже есть. И это первая вещь, которую любит делать компания Renovate. Это версии, которые допускают возможность использования нескольких версий до тех пор, пока основная версия все еще удовлетворяет требованиям. Программа Renovate действительно закрепляет зависимости.
Что значит закрепить зависимости? Это означает, что мы всегда будем работать с версией 8.1.1. У нас никогда не будет морковки. Я думаю, что так зовут этого персонажа. А затем 8.1.1. И на нашем компьютере у нас есть версия, допустим, 8.1.3. Но тогда в среде CI, поскольку мы проводим тесты немножко позже по времени, она будет работать с 8.2.0. И это кардинальные изменения.
Бывает так, что в CI происходит сбой, но он работает на нашей машине. И из-за этого нам нужно обновить зависимости на нашей машине. А это может быть трудно отладить. Так что закрепление зависимостей никогда не бывает очень плохим делом до тех пор, пока у нас есть автоматизированный инструмент управления зависимостями.
Если у нас нет автоматизированного инструмента управления зависимостями, то достаточно трудоемко вручную обновлять каждый отдельный номер здесь, потому что они закреплены. И нам нужно обновить их вручную.
Позаботившись об этом, мы можем просто пойти дальше и определить эти зависимости. Это также гарантирует, что с этого момента каждый раз, когда вы клонируете репозиторий и запускаете установку npm, будут устанавливаться именно те зависимости, с которыми я работаю.
Я думаю, что это действительно очень позитивно для нас, потому что это гарантирует, что мы работаем именно с теми зависимостями, с которыми я работаю. Одни и те же посылки. Так что это определенно то, чего мы хотим в этом проекте.
Я просто подойду сюда. Ваш вопрос объединяется. Подтверждаю – ваш вопрос объединяется. Просто идеально.
Теперь нам нужно еще раз вытащить Мастер-файл, потому что зависимости были обновлены.
И как вы можете видеть, Dependabot уже начинает правильно идентифицировать зависимости нашего каталога авторизации.
Мы не добавляли к нему ни пути, ничего-либо еще.
Упсс, как я уже сказал, я думаю о зависимости. Но я имею в виду обновление. Извините, я напутал. Как вы можете видеть, нам не нужно добавлять какой-либо путь к нашему обновлению. Это файл в формате json. Он достаточно умен, чтобы идентифицировать пакет.
Json находится в нашем каталоге «Auth».
Если мы захотим исключить какой-либо каталог в будущем, у нас также есть возможности исключить определенный каталог из процесса сканирования при обновлении. Но на данный момент нам действительно не нужно беспокоиться об этом.
Так что, вернувшись к моему терминалу, давайте проверим главную ветвь. Вытащим вот это, а затем сольем это в наш Renovate.
Итак, я вернулся к своей среде разработки. Я заметил одну вещь. Renovate закрепляет только зависимости разработчиков. Это не означает закрепление самих зависимостей. И это происходит потому, что именно так работает автоматическая стратегия обновления, когда она обновляет зависимость.
Так что если я перейду к приведенной здесь документации, мы увидим, что автоматическая стратегия обновления работает примерно также для nmp.
Что касается nmp, то всегда найдется другой пакет, в котором она работает по-другому. Так что он всегда будет фиксировать зависимости разработчиков. И будет фиксировать зависимости, если они обнаружат, что это приложение, а не библиотека.
В нашем случае это действительно приложение. Но оно не определяет, что это приложение.
Мы перейдем к файлу конфигурации и точно определим стратегию для этой стратегии диапазона. Ключ стратегии диапазона мы добавим вот сюда. И будем указывать pin-код вместо значения по умолчанию. Так что мы будем использовать здесь это поведение с pin-кодом.
Давайте скопируем это и вернемся в среду разработки и добавим в наш конфигурационный файл.
Итак, в renovate.json я могу добавить ключ. И здесь будет написано, что мы будем использовать pin-код. И если у меня действительно нет правильно значения, он предупредит меня, что значение должно быть одним из значений «auto», «pin», «bump» и т. д. Это означает, что мы добавляем стратегию диапазона на нужном уровне. Все в порядке. Я сохраню это.
Давайте вернемся к терминалу. Зафиксируем это. Нажмем на эту ветку, а затем сольем это в Мастер. И посмотрим, создаст ли Renovate PR для фактического закрепления зависимости из нашего приложения.
Вернувшись к своему терминалу, я просто очищу выходные данные. Добавлю все необходимое, зафиксирую сообщением update Renovate config.
И как только все тесты пройдут, и изменения будут зафиксированы, я отправлю это сообщение в удаленное хранилище.
Вернувшись в удаленное хранилище, я создам запрос на извлечение из программы Renovate. У нас должна быть возможность объединиться. Никаких изменений не произойдет.
Вот здесь я создам этот запрос на вытягивание и автоматически объединю его. Я просто подожду, пока пройдут тесты. Тесты должны начаться здесь в ближайшее время. Как только они будут завершены, как только checks станут зелеными, я просто солью все это в программу Мастер. Просто идеально.
Давайте сольем это воедино, а затем извлечем последнюю версию программы Мастер. И сольем ее обратно в программу Renovate, потому что мы все равно продолжим работать над конфигурацией.
Вернувшись к своему терминалу, я только что снова очистил выходные данные. Оформите заказ в главном пуле. И как вы можете видеть, у нас здесь появилось довольно много новых филиалов компании Renovate.
Давайте заглянем в Мастер слияний филиалов Renovate. Вообще-то здесь мы могли бы сделать перебазирование, но, в общем-то, все в порядке. А затем мы нажимаем на пульт дистанционного управления. Прежде чем мы вернемся и проверим систему PR обновления, мы хотим завершить настройку программы обновления.
Вот файл в формате json. Помимо того, что у нас есть pin-код для стратегии диапазона, мы также хотим изменить базовую ветвь для PR Renovate. И мы хотим включить автоматическое слияние всякий раз, когда у нас появляется незначительное обновление или патч-обновления.
Хорошо, давайте поступим именно так. Здесь я могу сказать – базовая ветвь. Базовые ветви будут представлять собой массив. И чтобы убедиться, что мы правильно это реализуем, давайте вернемся к документации и посмотрим, как они упоминают пример базовых ветвей.
Таким образом, базовые ветви действительно представляют собой массив, потому что может случиться так, что у нас будет несколько потоков выпуска. Они говорят, что если у нас есть более одной ветки выпуска и мы хотим поддерживать их все в актуальном состоянии, тогда мы можем просто добавить более одной ветки в эти базовые ветви.
В нашем случае у нас есть только одна ветвь, которая нам нужна.
Давайте вернемся к файлу понятий, и это будет ветвь обновления зависимостей. Я скопирую это, и, вернувшись в свою среду разработки, просто добавлю это в массив. Все в порядке.
Теперь мы позаботимся о настройке базовых ветвей. Давайте займемся настройкой автоматического слияния.
Я возвращаюсь к параметрам конфигурации программы Renovate. И это именно то, чего мы хотим. Они уже упоминали об этом. Вы можете настроить программу Renovate таким образом, чтобы она автоматически объединяла все обновления кроме основных. Это означает, что она автоматически объединит незначительные обновления: обновления исправлений, обновлений pin-кода и обновление degest. И это в значительной степени именно то, чего мы хотим, потому что мы хотим сократить рабочую нагрузку по управлению нашими зависимостями.
Так что я просто скопирую это сюда и, вернувшись в свою среду разработки, добавлю это сюда. Упсс, мне просто нужно удалить вот это и вот это. И это именно то, чего мы хотим. Так что я сохраню вот это. И этого будет достаточно для нашей конфигурации.
Мы зафиксируем эти изменения и сольем их в Мастер. А затем посмотрим, что будет происходить с PR-сервисами из Renovate. Вернувшись к своему терминалу, позвольте мне еще раз очистить выходные данные и проверить, что мы изменили файл. Так что я добавлю это обновление ядра обновляющее конфигурацию. И, возможно, этот single не сработает. Так что я просто зафиксирую его вот так и дождусь прохождение теста. Это должно произойти относительно быстро. И тогда я смогу перенести изменения в удаленный репозиторий, а затем открыть оттуда PR-страницу.
Возвращаясь к своим запросам на извлечение, я нажму здесь на новый запрос на извлечение и на обновление. Тогда я могу проверить, есть ли какие-то значимые изменения. Я создам запрос здесь и еще раз скажу «Обновить конфигурацию ядра».
И как вы можете видеть, сразу после того, как мы объединили PR, обновление автоматически закрыло и открыло PR, потому что мы изменили некоторые конфигурации базовой ветви и то, как она будет управлять автоматическим объединением. Так что программа Renovate уже позаботилась об этом, автоматически обновляя учетные записи пользователей, которые открываются после объединения новой конфигурации.
На данный момент у нас нет открытых учетных записей пользователей, потому что программа Renovate обрабатывает новую конфигурацию. Но скоро мы начнем видеть, как некоторые из них появляются здесь. А затем мы сможем вернуться и проверить, о чем именно они говорят.
После того, как я довольно долго ждал обновлений, и ничего не получил от Renovate, мне стало интересно, что происходит.  И хорошо, если мы сохраним это расширение здесь. Это расширяет базу конфигурации. В конфигурации возникнут некоторые конфликты. И не совсем ясно – будет ли это новые конфигурации, которые переопределяют расширенные конфигурации. Или это расширенные конфигурации, которые переопределяют конфигурации, которые мы здесь пишем.  
Так что я удалил эту информацию из файла. Таким образом, мы начали видеть новые рекламные объявления от компании Renovate. Так что давайте вернемся на GitHub и объединим некоторые из них.
Первый шаг заключается в том, чтобы обновить или закрепить зависимости в нашем массиве зависимостей. Так что речь идет не о зависимостях разработчиков, а о производственных зависимостях. И это то, как я уже упоминал, мы хотим сделать специально.
Если вы находитесь в других сценариях, где наличие семантического управления версиями зависимостей является преимуществом, то во что бы то ни стало продолжайте. И сохраните эту конфигурацию без каких-либо проблем.
Но я думаю, что здесь вам будет гораздо легче следить за ходом работы, если у нас будут установлены точно такие же зависимости.
Еще один комментарий заключается в том, что теперь базовая ветвь – это ветвь обновления зависимостей. Поэтому я подойду сюда и создам новый запрос на извлечение для Мастера.
Обновление зависимостей обновляется примерно так. А затем я увижу, что все в порядке. Я изменил здесь некоторые файлы и солью их в Мастер-файл, чтобы Мастер был обновлен до последней версии.
Вот так вот создайте запрос на вытягивание. И здесь я задам прямой вопрос о слиянии. Честно говоря, я мог бы подождать тестов, но поскольку это всего лишь простые задачи управления зависимостями, то я почти уверен, что мое приложение останется неизменным, так что все тесты будут пройдены.
Конечно, в производственной среде ветка была бы защищена. И на самом деле она должна быть защищена. Но я отключил защиту для этого видео, чтобы мы могли немного ускорить процесс. В противном случае потребовалось бы слишком много времени, пока все проверки были бы пройдены. И все отдельные обновления и PR были созданы, обновились. Так что для этого видео я отключил защиту главной ветки, после чего активирую ее снова.
Как вы можете видеть, от компании Renovate поступило 14 открытых запросов на извлечение данных. А это значит, что у нас уже есть множество пакетов, которые могут быть обновлены в нашем проекте. Именно здесь мы начинаем понимать реальную мощь и насколько полезно автоматизированное управление зависимостями. Вот и все, что нужно для этого видео. 