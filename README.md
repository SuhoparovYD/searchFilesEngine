# searchEngine
Поисковый движок.

Предназначен для быcтрого поиска по текстовым файлам.

В конфигурационном файле перед запуском приложения задаются названия файлов, по которым движок будет осуществлять поиск.

Движок индексирует все файлы так, чтобы быстро находить наиболее релевантные документы.

Пользователь задаёт запрос через JSON-файл requests.json. Запрос — это набор слов, по которым нужно найти документы.

Программа формирует файл answers.json, в который записывает результаты поиска.

Программа собрана со статическим включением библиотек.

Файлы:

searchEngine.exe, исполняемый файл;

GtestTests.exe, тесты;

config.json, файл конфигурации (обязателен);

resources, папка с документами;

requests.json, запрос к поисковому движку.

Описание работы с программой.

Программа может работать как служба или процесс , (завершение с клавиатуры не предусмотрено - достаточно закрыть окно).

При запуске считывается файл config.json, далее загружается файл запроса requests.json и формируется ответ - answers.json. Есть возможность работать в режиме приложения, или перейти в "серверный" режим, в котором :

 - проверяется требование обработки запроса - отсутствие файла answers.json, (при его отсутствии запускается обработка поискового запроса - requests.json и создается файл ответа - answers.json). Таким образом для запроса к поисковику достаточно записать новый запрос (файл request.json, можно поверх), и удалить(или переименовать) файл answers.json;
 - анализируется условие пересоздания индекса - одновременное отсутствие файлов request.json и answers.json. Для чего достаточно удалить(или переименовать) файл requests.json, затем удалить (или переименовать) файл answers.json. (До этого должен быть выполнен хотя бы оди запрос на предыдущей версии индекса, что происходит автоматически при появлении requests.json)
 - ведется обработка ошибок файла запросов (request.json)
