# Оставляем заметки

Проект представляет собой набор скриптов для работы с онлайн органайзером [Evernote](https://evernote.com/intl/ru).
Они позволяют создавать заметки и проверять входящие сообщения.


## Как установить
- Для работы скриптов необходимо зарегистрироваться на сайте, после чего заполнить `.env` файл необходимыми данными 
[со страницы с документацией](https://dev.evernote.com/doc/) по такому принципу:
```commandline
EVERNOTE_CONSUMER_KEY=Получить можно, нажав на GET AN API KEY, после заполнения данных об аккаунте
EVERNOTE_CONSUMER_SECRET=Выдается вместе с Consumer key
EVERNOTE_PERSONAL_TOKEN=Получить можно в разделе OAuth

JOURNAL_TEMPLATE_NOTE_GUID=Код шаблона заметки получаем из адресной строки https://evernote.com/...n=[Нужный вам код здесь]&...
JOURNAL_NOTEBOOK_GUID=Получить можно после создания блокнота, при запуске скрипта list_notebooks.py

INBOX_NOTEBOOK_GUID=Получить можно так же после создания блокнота, при запуске скрипта list_notebooks.py

SANDBOX=True или False (в зависимости, от того где используется приложение, на тестовом сервере "песочница" или на основном)
```
- Для корректной установки зависимостей должен быть установлен Python3. 
- Установите зависимости командой pip (или pip3, если есть конфликт с Python2):
```commandline
pip install -r requirements.txt
```

## Как запустить

### list_notebooks.py
После выполнения, скрипт выводит список Guid ваших блокнотов, которые можно использовать в качестве `INBOX_NOTEBOOK_GUID` или `JOURNAL_NOTEBOOK_GUID`

Запустите основной скрипт командой python (или python3):

```commandline
python list_notebooks.py
```
Пример выполнения:

```commandline
f1efeca2-8ec4-45d3-80d1-665b83de9625 - Первый блокнот
1324d924-cc32-4156-9821-accacebac3f0 - Входящие сообщения
```


### config.py
Вспомогательный файл, в котором находятся настройки данных guid, названия переменных, кодировка текста и название файла с переменными окружения.
Соответственно, все данные будут контролироваться через `.env` файл.


Запуска не требует.


### dump_inbox.py
После выполнения, скрипт выводит список записок в блокноте, используемом в качестве входящих сообщений/заметок (актуально при работе в команде,
можно настроить доступ определенному кругу людей)

Запустите основной скрипт командой python (или python3):

```commandline
python dump_inbox.py
```
Пример выполнения:

```commandline
--------- 1 ---------


Первая заметка в Inbox

--------- 2 ---------


Вторая заметка во Inbox
```

### add_note2journal.py
После выполнения, скрипт создаст запись в личном журнале с guid `JOURNAL_NOTEBOOK_GUID`, по созданному вами шаблону и указанному в 
`JOURNAL_TEMPLATE_NOTE_GUID`.

Запустите основной скрипт командой python (или python3):

```commandline
python add_note2journal.py
```
Пример выполнения:

```commandline
Title Context is:
{
    "date": "2022-11-10",
    "dow": "четверг"
}
Note created: meeting
Done
```


## Цель проекта
Код написан в образовательных целях на онлайн-курсе для веб-разработчиков [Devman](https://dvmn.org).
