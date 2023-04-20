# Шаг 0 «Вход в SAP Build лобби» {#шаг-0-вход-в-sap-build-лобби .unnumbered}

1.  Откройте <https://samruktest-gdpazdel.eu10.build.cloud.sap/lobby>\
    аутентифицируйтесь
    через **https://a8nbw3y7x.accounts.ondemand.com/**.

![](media/image1.png){width="6.5in" height="2.254861111111111in"}

2.  Введите ваши логин и пароль пользователя

![](media/image2.png){width="6.5in" height="4.425694444444445in"}

# Шаг 1 «Создание проекта приложения в SAP Build apps Lobby»: {#шаг-1-создание-проекта-приложения-в-sap-build-apps-lobby .unnumbered}

Создайте проект вашего приложения нажав **Create**.\
\
![Create the project](media/image3.png){width="6.5in"
height="2.8895833333333334in"}

> Выберите **Build an Application**.\
> \
> ![Build App](media/image4.png){width="6.5in"
> height="3.2569444444444446in"}
>
> Далее **Web & Mobile Application**\
> \
> ![Name the project](media/image5.png){width="6.5in"
> height="3.252083333333333in"}
>
> для Project Name задайте имя на основе вашего юзера
> **mobile_app_ws_user?,** добавьте комментарий в описание и нажмите\
> **Create**, чтобы начать работать над приложением.\
> \
> ![](media/image6.png){width="6.5in" height="5.901388888888889in"}

# Шаг 2 «открытие проекта, домашняя страница»: {#шаг-2-открытие-проекта-домашняя-страница .unnumbered}

Вы будете перенаправлены на редактор Build Apps Composer, который
представляет своего рода IDE для SAP Build Apps. На канве вы уже можете
видеть первоначальную страницу приложения **Home page** с полями
заголовка и текста:\
![](media/image7.png){width="6.5in" height="3.6222222222222222in"}

> Слева располагаются элементы, которые могут быть добавлены на канву.
> Справа располагается панель свойств выбранного элемента, снизу справа
> расположена структура элементов на канве. Снизу панель добавления
> логики к элементам.
>
> В целом, построение приложения заключается в:
>
> \- определении подключений источников данных, переменных приложения
>
> \- UI элементов
>
> \- логики работы выбранных элементов

# Шаг 3 «Архитектура приложения: подключение к данным»: {#шаг-3-архитектура-приложения-подключение-к-данным .unnumbered}

Пройдем во вкладку **DATA**:

![](media/image8.png){width="6.5in" height="3.417361111111111in"}

Далее в секции SAP Build Apps classic data entities создадим определение
2х API вызовов типа OData Integration.

1.  Один - API вызов для получения данных о заявке на проход по UUID,
    считанного из QR кода.

2.  Второй - API вызов для загрузки изображения в Blob таблицу по UUID,
    считанного из QR кода.

Для этого, выберем **OData Integration** тип:

![](media/image9.png){width="6.4875in" height="3.8069444444444445in"}

Вставим ссылку описания наших API сервисов (\$metadata) от сервера API:

<https://afanasevdm-cfruntime-371tohiy-dev-dbapi-fiori-srv.cfapps.us10.hana.ondemand.com/service/catalog/$metadata>

нажмем **Verify URL**:

![](media/image10.png){width="6.5in" height="4.731944444444444in"}

Конфигуратор по описанию metadata информации распознал 2 сущности:
**Request, Blobstorage**, активируем обе:

![](media/image11.png){width="6.5in" height="4.764583333333333in"}

Для сущностей появляются элементы настройки стандартных методов доступа
к ним (GET, POST, UPDATE и т.д.). Сохраняем конфигурации нажатием SAVE
DATA RESOURCES:

![](media/image12.png){width="6.5in" height="4.8in"}

В результате у нас появились в проекте описанные методы доступа к 2
сущностям API сервера: Request (таблица заявок) и Blobstorage (таблица
blob объектов c UUID заявки).

Результат:

![](media/image13.png){width="6.5in" height="3.4298611111111112in"}

# Шаг 4 «Архитектура приложения: создание страниц приложения»: {#шаг-4-архитектура-приложения-создание-страниц-приложения .unnumbered}

Согласно архитектуре приложения, нужно создать 2 страницы приложения
«Home Page» и "Photo Page". Для этого кликните по ссылке "Home Page":

![](media/image14.png){width="6.5in" height="3.2180555555555554in"}

Откроется конфигуратор, где необходимо добавить вторую страницу, кликнув
на **ADD NEW PAGE**:

![](media/image15.png){width="6.5in" height="3.4208333333333334in"}

В открывшемся окне введите название страницы «**Photо page**», далее
**OK**:

![](media/image16.png){width="6.5in" height="2.192361111111111in"}

В результате откроется вновь созданная страница, нажмите SAVE:

![](media/image17.png){width="6.5in" height="3.2423611111111112in"}

# Шаг 5 «Архитектура приложения: добавление элементов первой странички»: {#шаг-5-архитектура-приложения-добавление-элементов-первой-странички .unnumbered}

1.  

Переходим на первую страницу приложения, кликнув **Home page** по
навигационной ссылке и потом по самой страничке **Home page**: (может
потребоваться нажать SAVE, если предыдущие изменения не были сохранены)

![](media/image18.png){width="6.5in" height="3.4256944444444444in"}

![](media/image19.png){width="6.5in" height="3.982638888888889in"}

Выберите Headerline и измените текст на следующий «***Наведите на QR код
заявки в приложении***»:

![](media/image20.png){width="6.5in" height="2.9791666666666665in"}

В **LAYOUT** вкладке свойств в разделе **LAYOUT** выберите выравнивание
по центру:

![](media/image21.png){width="6.5in" height="4.131944444444445in"}

и удалите второй **Text 1** элемент:

![](media/image22.png){width="6.5in" height="3.5756944444444443in"}

2\.

Добавьте элемент **Button** на канву первой странички из библиотеки
элементов слева, вкладка **CORE**. поменяйте название кнопки ***"Scan
QR"***:

![](media/image23.png){width="6.5in" height="2.6381944444444443in"}

Выставьте свойство выравнивание от верхнего края в **LAYOUT -\>
POSITION** вкладке свойств **Button 1**:

![](media/image24.png){width="6.5in" height="3.9006944444444445in"}

В фомуле введите значение
«***systemVars.dimensions.viewport.height\*0.5***», далее **SIBMIT**:

![](media/image25.png){width="6.5in" height="3.1125in"}

А так же

![](media/image26.png){width="6.5in" height="3.9833333333333334in"}

# Шаг 6 «Архитектура приложения: добавление логики первой странички»: {#шаг-6-архитектура-приложения-добавление-логики-первой-странички .unnumbered}

1\.

Определим переменную **uuid_var** уровня App Variable с типом *"**any
text**"*, куда будет считан UUID заявки, переключив **VIEW --
VARIABLES**:

![](media/image27.png){width="7.059271653543307in"
height="2.3319324146981626in"}

Сохраним изменения через **SAVE**

Перейдем на первую страницу приложения "**Home page**", переключив
**VIEW -- VARIABLES**.

Выберем кнопку **Scan QR**, откроем панель **Add logic to "Button 1"**
внизу экрана:

![](media/image28.png){width="6.488888888888889in"
height="3.3208333333333333in"}

и разместим в открывшейся панели следующие элементы с панели **Logic
CORE** слева:

#### Device: Scan QR/barcode

#### Variables: Set app variable

#### Data: Get Record

#### Navigation: Open page

#### Dialog: Alert

#### Dialog: Alert

И соединим их как показано на рисунке:

![](media/image29.png){width="6.5in" height="2.964583333333333in"}

В логическом блоке **Variables: Set app variable** присвоим переменной
**uuid_var** уровня App Variable считанное и дешифрованное значение из
блока **Scan QR/barcode** привязав значение переменной в поле **Variable
name**:

![](media/image30.png){width="6.5in" height="2.9881944444444444in"}

И присвоив значение вывода предыдущего блока, кликнув на иконку под
**Assigned value** и выбрав **Output value of another node**:

![](media/image31.png){width="6.491666666666666in" height="3.58125in"}

Далее выбрать **Scan QR/barcode** у Select logic node, **Scan QR/barcode
/ QR barcode content** у Select node output, далее кнопка **SAVE**:

![](media/image32.png){width="6.497222222222222in"
height="4.497222222222222in"}

Для чтения данных по заявке методом **Get record** используя
дешифрованное значение UUID, хранящееся в переменной **uuid_var**,
заполняем параметры блока следующим образом:

\- API вызов из ресурса **Request**:

![](media/image33.png){width="6.5in" height="3.676388888888889in"}

Id параметр заполняется переменной:

![](media/image34.png){width="6.4944444444444445in"
height="3.9291666666666667in"}

Далее **App Variables**, дальше выбираем переменную **uuid_var** и жмем
**SAVE**:

![](media/image35.png){width="6.5in" height="4.973611111111111in"}

Для первого элемента **Alert** задаем текст «**cannot read QR**» вывода
при неудачном чтении QR кода:

![](media/image36.png){width="6.5in" height="3.3680555555555554in"}

Для второго **Alert** аналогично задаем сообщение неуспешного чтения из
API -- "**request not found**":

![](media/image37.png){width="6.5in" height="4.0256944444444445in"}

Сохраняем все изменения в проекте через кнопку SAVE:

![](media/image38.png){width="6.5in" height="1.9979166666666666in"}

# Шаг 7 «Архитектура приложения: добавление переменных и элементов второй странички»: {#шаг-7-архитектура-приложения-добавление-переменных-и-элементов-второй-странички .unnumbered}

Переходим на страницу Photo page:

![](media/image39.png){width="6.5in" height="3.676388888888889in"}

Переключитесь в режим **VARIABLES** и добавьте 2 переменные **name** и
**surname** как параметры страницы на вкладке **PAGE PARAMETERS**:

![](media/image40.png){width="6.497222222222222in"
height="2.3152777777777778in"}

Перейдите на вкладку **PAGE VARIABLES** и создайте еще 2 переменные для
хранения сделанной фотографии с соответствующими типами данных (mimetype
-- text; photo_path -- local file system path):

![](media/image41.png){width="6.5in" height="1.913888888888889in"}

Перейдите в режим VIEW и удалите **Headline** элемент. А для текстового
элемента задайте свойство Content в виде формулы:

![](media/image42.png){width="6.5in" height="3.66875in"}

И значение формулы - **JOIN(\[\"Сделайте фото для \", params.name,
params.surname\], \' \')**:

![](media/image43.png){width="6.5in" height="3.6756944444444444in"}

Расположите текст по центру, поменяв свойства тестового поля как на
картинке **LAYOUT -\> Text Align -\> center**:

![](media/image44.png){width="6.5in" height="2.120138888888889in"}

Далее добавьте на канву элементы:

\- Image

\- Button 1

\- Button 2

Поменяйте label для кнопок как на картинке:

![](media/image45.png){width="6.5in" height="3.6465277777777776in"}

Для элемента Image увяжите свойство **Source** картинки с переменной
**PAGE VARIABLE: photo_path**:

![](media/image46.png){width="6.5in" height="3.854861111111111in"}

Далее поменяйте размеры картинки на фиксированные:

![](media/image47.png){width="6.5in" height="3.3881944444444443in"}

И расположите картинку по центру:

![](media/image48.png){width="6.5in" height="3.4569444444444444in"}

# Шаг 8 «Архитектура приложения: добавление логики работы второй странички -- кнопка take photo»: {#шаг-8-архитектура-приложения-добавление-логики-работы-второй-странички-кнопка-take-photo .unnumbered}

Выберем кнопку take a photo и откроем панель добавления логики и кликнем
на **Marketplace**:

![](media/image49.png){width="6.5in" height="3.3291666666666666in"}

В поле поиска напишем «covert file to base64» и выберем найденный
элемент:

![](media/image50.png){width="6.5in" height="2.308333333333333in"}

Далее установим компонент нажав **INSTALL**:

![](media/image51.png){width="6.5in" height="2.5277777777777777in"}

После этого, элемент появится во вкладке INSTALLED:

![](media/image52.png){width="5.861757436570429in"
height="3.2781386701662294in"}

Далее соберем следующие элементы на канве логики работы кнопки:

-   DEVICE: take photo

-   VARIABLES: set page variable

-   VARIABLES: set page variable

-   DIALOG: Alert

И свяжем как на картинке:

![](media/image53.png){width="6.5in" height="3.290277777777778in"}

Один элемент присвоения переменной увяжем с Mime type вывода элемента
Take photo и переменной страницы mimetype:

![](media/image54.png){width="6.497222222222222in"
height="4.059722222222222in"}

И сохранить.

Во втором элементе настроить присвоение страничной переменной photo_path
с выводом блока Take photo -- path:

![](media/image55.png){width="6.5in" height="4.2444444444444445in"}

И сохранить.

Для элемента **DIALOG: Alert** задайте текст "**failed to take photo**":

![](media/image56.png){width="6.5in" height="3.2958333333333334in"}

Сохраните проект:

![](media/image57.png){width="6.5in" height="1.7201388888888889in"}

# Шаг 9 «Архитектура приложения: добавление логики работы второй странички -- кнопка upload to system»: {#шаг-9-архитектура-приложения-добавление-логики-работы-второй-странички-кнопка-upload-to-system .unnumbered}

Выберем кнопку Upload to system и откроем панель логики работы кнопки.
Далее добавим след элементы на панель:

\- MEDIA: Convert file to base64 (чтобы сериализовать фото в
последовательность текста и сохоанить в виде BLOB в поле таблицы в БД)

\- VIEW: Show spinner (чтобы заморозить экран на время работы конвертера
и загрузки в БД)

\- VIEW: Show spinner (чтобы разморозить экран в случ успеха или ошибки)

\- DATA: Create record (чтобы передать в API параметры картинки и
сохранить в БД)

\- DIALOG: Alert (чтобы вывести сообщения об успехе или ошибки работы
процесса)

И увяжем их соответствующим образом:

![](media/image58.png){width="6.5in" height="2.3652777777777776in"}

Далее для элемента **Convert file to base64** зададим след параметры:
URL файла для конверсии укажем из **PAGE VARIABLE photo_path**:

![](media/image59.png){width="6.5in" height="3.540277777777778in"}

Для элемента Create Record выберем resource name: Blobstorage:

![](media/image60.png){width="6.5in" height="2.2534722222222223in"}

А для поля **Record** выберем «**Object with properties**» и зададим
след значения:

\- поле **mimetype** увязать с переменной **mimetype** типа **PAGE
VARIABLE**

\- поле **req_uuid** увязать с переменной **uuid_var** типа **APP
VARIABLE**

\- поле **Imagedata** увязать с выводом предыдущего элемента-конвертора
**Convert file to Base64 / Base64 text**

![](media/image61.png){width="6.497222222222222in"
height="4.097916666666666in"}

Для Alert успешного создание записи в БД выводим сообщение успеха -
***Uploaded***:

![](media/image62.png){width="6.5in" height="3.9923611111111112in"}

В случае неуспешной записи в БД выводим сообщение -- ***Failed to
Upload***:

![](media/image63.png){width="6.5in" height="4.221527777777778in"}

В случае неуспешной ковертации изображения выводим сообщение --
***failed to convert***:

![](media/image64.png){width="6.5in" height="3.783333333333333in"}

Сохраняем весть проект:

![](media/image65.png){width="6.5in" height="1.9638888888888888in"}

# Шаг 10 «Архитектура приложения: увяжем передачу параметров между страницами»: {#шаг-10-архитектура-приложения-увяжем-передачу-параметров-между-страницами .unnumbered}

Откроем страницу **Home page** и выберем кнопку **Scan QR**, откроем
панель логики работы кнопки и выберем блок **NAVIGATION: Open page**. В
свойстве page (следующей открываемой страницы) укажем страницу **Photo
page**:

![](media/image66.png){width="6.5in" height="3.14375in"}

А требуемые параметры открываемой страницы (PAGE PARAMETERS определенные
для Photo page ранее) увяжем с возвращенным результатом работы API Get
record к сущности Request:

![](media/image67.png){width="6.488888888888889in"
height="3.701388888888889in"}

И сохранить.

Сохраняем весть проект:

![](media/image65.png){width="6.5in" height="1.9638888888888888in"}

# Шаг 11 «Запуск приложения в тестовом режиме на телефоне»: {#шаг-11-запуск-приложения-в-тестовом-режиме-на-телефоне .unnumbered}

1.  Устанавливаем приложение **SAP Build Apps** из Appstore или Google
    Store

2.  Переходим на вкладку Launch в проекте приложения, далее **OPEN
    PREVIEW PORTAL**:

![](media/image68.png){width="6.5in" height="2.509027777777778in"}

3.  На моб телефоне заходим в приложение **SAP Build Apps**, выбираем
    вход через SAP Build Apps, далее 6ти значный код вводим на портале в
    браузере и жмем **Confirm**:

![](media/image69.png){width="6.5in" height="4.517361111111111in"}

4.  Далее на мобильном приложении в списке Apps находим свой проект и
    жмем **Open**. Приложение запускается
