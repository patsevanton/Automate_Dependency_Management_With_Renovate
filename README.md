А как вы справляетесь со своими зависимостями? Откуда вы знаете, что существует более новая версия какой-то зависимости? Когда вы обновляете свои зависимости, именно тогда вы обнаруживаете, что та или иная зависимость больше не поддерживается? Неужели именно тогда, когда она перестает работать? А, может быть, когда сканирование системы безопасности показывает вам, что существует мост? И что еще более важно, делаете ли вы это вручную? Вы переходите от одной зависимости к другой, а затем проверяете ее и периодически обновляете? Или у вас есть какая-то автоматизация?

Как насчет того, чтобы создать систему, которая будет создавать pull request с обновлениями для всех ваших зависимостей? А затем вы сможете выбрать – хотите ли вы обновить их все или некоторые из них. Это зависит только от вас.



Почему автоматизация управления зависимостей необходима даже для небольших проектов.

Если я добавлю цифры сейчас, они составят около 30 зависимостей, которыми нам нужно будет управлять вручную, если мы захотим обновить их, не имея решения автоматического управления. Это не подается масштабированию. Это отнимает много времени поддерживать все зависимости в актуальном состоянии. И речь идет только о микросервисе аутентификации.

Позже мы также добавим веб-клиент, добавим другие микросервисы и будем поддерживать все эти зависимости в актуальном состоянии. И на все это у нас нет времени.

Даже если мы были бы крупной компанией, имеющей большими ресурсами, это все равно было бы потрачено впустую, потому что оно может быть автоматизировано с помощью инструментов, которые уже существуют.

В чем заключается главная причина, по которой нам нужны автоматизированные зависимости? Конечно, есть и другие преимущества. Например, обновление для системы безопасности стоит очень дорого. Они применяются гораздо быстрее, чем, если бы мы постоянно отслеживали пакеты обновления для системы безопасности. Так что я почти уверен, что нет ни одного аргумента, который бы говорил: «Хорошо, нам не следует использовать автоматизированные решения для управления зависимостями».





Как мне узнать, что есть обновление зависимостями?

И я бы хотел, чтобы все это было максимально автоматизировано, потому что это утомительно, когда приходится постоянно обновлять зависимости вручную.

Вы определенно хотите иметь воспроизводимую установку. И поэтому вам нужно подумать, как это сделать. И поэтому закрепленные версии – хорошая идея.

Недостаток строго закрепленных версий в том, что ты зацикливаешься ровно на одной версии.

Возникает вопрос – что с этим делать? Первый вариант, чтобы вы регулярно запускали npm update.

Т. е. вы получите уведомление, когда появятся новые версии.

Но загвоздка в том, что кто-то должен выполнять эту команду на регулярной основе.

Это хорошо работает, когда над кодом регулярно работают. Но если долгое время с кодом ничего никто ничего не делал, то и обновление зависимостей не будет.

Это означает, что это хорошее решение, но не отличное. Поэтому нужно было сделать это автоматизированным способом, чтобы выполнялось регулярно.





Управление зависимостями в проектах – это огромная боль.

Даже относительно простые проекты часто содержат множество различных зависимостей и множество версий различных пакетов, расположенных в проекте.

Эти пакеты постоянно обновляются не только для того, чтобы предлагать новые функции, но и для устранения уязвимостей, которые появляются в этих пакетах с течением времени.

Даже если вы занимаетесь всего лишь одним или двумя проектами, накладные расходы на это могут быстро стать значительными. Если у вас много проектов, проблема становится еще хуже.



Случалось ли с вами, что с течением времени в ваших репозиториях на GitHub, Gitlab или где-то бы ни было, зависимости постоянно обновляются, пока вы погружены в проект, либо во время технического обслуживания.

Проходит некоторое время, вы работаете над другим проектом. И внезапно в предыдущем проекте появляются 
исправления ошибок (включая исправления безопасности). Как вам узнавать об обновлениях (включая 
исправления безопасности)? Как патчить проект, если вы не запускаете CI/CD pipeline?

Иногда обнаруживается, что вы пользуетесь библиотеками, в которых есть 
уязвимости, потому что никто не приступал к обновлению в течение нескольких месяцев, потому что специалист по безопасности не может уследить за всем, потому что внедрение devsecops практик у вас только планах.


