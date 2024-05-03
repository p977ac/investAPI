# Идентификация торговых инструментов

Для точного определения торговых инструментов используются разные идентификаторы: 

<ol>
<li><p><strong>Isin</strong> (International Security Identification Number) — международный 
идентификационный номер ценной бумаги. Состоит из 12 символов цифр и латинских букв, 
которые обычно начинаются с 2-буквенного кода страны эмитента ценной бумаги.  </p>
<p><strong>Структура ISIN</strong><br>Первые два символа — буквы, определяющие код страны эмитента согласно стандарту ISO 3166-1 — например, российские ISIN-коды начинаются буквами RU.<br>Далее следуют 9 букв и цифр национального идентификационного кода ценной бумаги (National Securities Identifying Number, NSIN).
Завершает код контрольная цифра. Например, ISIN акции TCS Group — US87238U2033.</p>
</li>
<li><p><strong>Ticker</strong> — краткое (1–5 букв) наименование ценной бумаги на конкретной бирже. Без 
указания биржи и режима торгов, по сути, является бессмысленным набором букв. Для этого 
на российских биржах MOEX и SPBE используется специальный признак &quot;Режим торгов&quot;, 
который соответствует техническому термину class_code. Комбинация тикера и class_code
является уникальным идентификатором, только тикер — нет.<br>Например, тикер TCS Group Tinkoff — TCSG.</p>
</li>
<li><p><strong>FIGI</strong> (Financial Instrument Global Identifier) — глобальный идентификатор 
финансового инструмента. Представляет собой 12-символьный код из латинских букв и цифр.
Определяется как идентификатор ценной бумаги на торговой площадке (бирже), которая 
является некоторым «источником цен».</p>
</li>
</ol>
<p>FIGI, присваемые в Тинькофф Инвестициях, не всегда совпадают с международным классификатором. 
Это устаревший параметр, который не рекомендуется использовать.</p>

## Идентификаторы из модели финансовых инструментов Тинькофф Инвестиций

В Тинькофф Инвестициях применяется иерархическая система идентификации финансовых объектов.

**Бренд**

На верхнем уровне находится **бренд** — работающая на финансовом рынке компания, являющаяся эмитентом ценных бумаг. Пример
бренда — Сбербанк. 

**Актив**

У бренда может несколько финансовых инструментов: акции (в том числе на разных биржах), облигации и прочее. Каждая из
ценных бумаг называется **актив**. 

**Позиция**

Один и тот же актив может торговаться на разных биржах, совокупность актива и торговой площадки (биржи) — это **позиция**.
В некоторых ситуациях размещение бумаг на бирже, выплаты купонов и дивидендов проходят позициям, которые отличаются от тех, 
что торгуются на бирже или находятся в портфеле.

**Торговый инструмент**

Одна и та же позиция может торговаться в разных режимах торгов и по разной цене. Например, валюта разной лотности может
иметь различную стоимость; акцию можно продать на биржевом и внебиржевом рынках, то есть в торговле на выходных.

Но одна и та же позиция может торговаться в разных режимах торгов и по разной цене: например: валюта разной лотности может иметь различную стоимость; или акцию можно продать как на биржевом рынке, так и на внебиржевом (в торговле на выходных).
Поэтому есть еще один идентификатор - **торговый инструмент** - он определяется как ценная бумага на торговой площадке (бирже) в указанном режиме торгов. Получить котировки можно только по торговому инструменту.

## Параметры в API

- `uid` бренда — идентификатор компании.
- `asset_uid` — идентификатор актива.
- `position_uid` — идентификатор позиции.
- `instrument_uid` — идентификатор торгового инструмента.

### Instrument_Id

Для удобства клиентов, которые в своих системах использовали устаревший идентификатор FIGI, в большинстве методов Tinkoff Invest
API предусмотрено универсальное поле **Instrument_Id** — в нём можно передавать как `FIGI`, так и `instrument_uid`.

Вы можете получить идентификаторы конкретного инструмента через метод [FindInstrument](/investAPI/instruments/#findinstrument), передав в параметре `query`
известный идентификатор или название инструмента.

Предпочтительнее использовать `Instrument_Id`, потому что это предполагает возможность использования
**instrument_uid** или **FIGI**.

Сейчас при передаче значения в параметре `Instrument_Id` сначала выполняется поиск инструмента по 
**instrument_uid**, потом — по **FIGI**.

Основной идентификатор торгового инструмента при работе с Tinkoff Invest API — UID, так как, например, в 
опционах идентификатор FIGI не поддерживается.