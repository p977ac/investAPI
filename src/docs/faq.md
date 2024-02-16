####[Можно ли вывести в API показатели компаний/прогнозы/доходности и т.д.?](#6.1)  
####[Какие документы регламентируют юридическую сторону работы API? ](#6.2)  
####[Как открыть дополнительные брокерские счета для использования в TINKOFF INVEST API?](#6.3)  
####[Какая логика работы с мультисчетами?](#6.4)  
####[Поддерживаются ли сейчас мультисчета в TINKOFF INVEST API?](#6.5)  
####[Поддерживает ли TINKOFF INVEST API работу с внебиржевыми инструментами?](#6.6)  
####[Торговля бумагами Тинькофф через TINKOFF INVEST API](#6.7)
####[Валюты в TINKOFF INVEST API](#6.8)

Ответы на часто задаваемые вопросы, относящиеся к работе различных сервисов TINKOFF INVEST API

* [FAQ Сервиса аккаунтов](/investAPI/faq_users/)
* [FAQ Сервиса инструментов](/investAPI/faq_instruments/)
* [FAQ Сервиса торговых поручений](/investAPI/faq_orders/)
* [FAQ Сервиса операций](/investAPI/faq_operations/)
* [FAQ Сервиса котировок](/investAPI/faq_marketdata/)
* [FAQ Сервиса стоп-заявок](/investAPI/faq_stoporders/)
* [FAQ Песочница](/investAPI/faq_sandbox/)


##Условия использования

###Можно ли сделать публичный сервис на основе TINKOFF INVEST API?
Нет, TINKOFF INVEST API предоставляется только клиентам Тинькофф без права на ретрансляцию данных.

###Можно ли вывести в API показатели компаний/прогнозы/доходности и т.д.? <a id="6.1"></a>

Пока не имеем права выгружать эти данные для автоматизированных систем. Работаем над этим.

###Какие документы регламентируют юридическую сторону работы API? <a id="6.2"></a>

Сервис предоставляется в соответствии с [пользовательским соглашением](https://www.tinkoff.ru/about/documents/disclosure/).

###Как открыть дополнительные брокерские счета для использования в TINKOFF INVEST API? <a id="6.3"></a>

Дополнительные счета Тинькофф Инвестиций открываются в мобильном приложении. Сделать это 
через TINKOFF INVEST API нельзя.

###Какая логика работы с мультисчетами? <a id="6.4"></a>

Каждый новый счет полностью изолирован от остальных - портфолио, операции, лимиты,
гарантийные обеспечения, уровни достаточности средств учитываются по каждому счету
отдельно. Поэтому может быть ситуация, при которой на одном счете средств хватает с
избытком, а на другом при нехватке средств и активной маржинальной торговле может
наступить маржин-колл.

###Поддерживаются ли сейчас мультисчета в TINKOFF INVEST API? <a id="6.5"></a>

Да, в TINKOFF INVEST API можно работать с несколькими счетами. Все ключевые методы принимают
на вход параметр *account_id* (идентификатор счёта).

###Поддерживает ли TINKOFF INVEST API работу с внебиржевыми инструментами? <a id="6.6"></a>

В данный момент TINKOFF INVEST API предполагает работу только с биржевыми инструментами.

###Торговля бумагами Тинькофф через TINKOFF INVEST API <a id="6.7"></a>

Из-за огромного количества скальперских сделок мы ограничили торговлю БПИФ от УК "Тинькофф Капитал"
в TINKOFF INVEST API. В данный момент действует ограничение в **100 сделок с этими бумагами в сутки**.

###Валюты в TINKOFF INVEST API <a id="6.8"></a>

Получить список доступных валют можно при помощи метода [getInstruments/currencies](/investAPI/instruments#currencies).

Обратите внимание, что лотность валют ограничена лотностью, которую предоставляет биржа. Например, по евро и доллару 1 лот равен 1000 единиц валюты.