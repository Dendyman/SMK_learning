# Step 0 «Enter SAP Build Lobby»

Open <https://samruktest-gdpazdel.eu10.build.cloud.sap/lobby>\
Authentificate using <https://a8nbw3y7x.accounts.ondemand.com/>
(only if the authentification is requested)

![](./media/image1.png)

Enter your user and password

![](./media/image2.png)

# Step 1 «Creating an Application Project in SAP Build apps Lobby»: 

Create your application project by clicking on **Create**.\
![Create the project](./media/image3.png)

Choose **Build an Application**.\
\
![Build App](./media/image4.png)

Next, select **Web & Mobile Application**\
![Name the project](./media/image5.png)

For the *Project Name*, specify a name based on your user, such as **mob_app_ws_user(?),** add a comment in the description, and then click **Create** to initiate working on your application.\
\
![](./media/image6.png)

# Step 2 «Opening the Project, Home Page»: 

Upon completing Step 1, you will be redirected to the Build Apps Composer editor, which serves as a kind of IDE (Integrated Development Environment) for SAP Build Apps. On the canvas, you can already see the initial **Home page** of your application with fields for the title and text:\
![](./media/image7.png)

On the left, you will find elements that can be added to the canvas. On the right, there is a properties panel for the selected element, and at the bottom right, you will find the structure of elements on the canvas. Below, there is a panel for adding logic to the elements.

In summary, building your application involves:

\- Defining connections to data sources and application variables.

\- Designing UI elements.

\- Implementing logic for the selected elements.


# Step 3 "Application Architecture: Data Connectivity":

In this step, we will focus on connecting our application to data sources. Follow the instructions below:

1. Navigate to the **DATA** tab:
   ![](./media/image8.png)

2. In the SAP Build Apps classic data entities section, create definitions for two API calls of type OData Integration:

   - One API call is for retrieving data about a request by its UUID, which is read from a QR code.
   
   - The other API call is for uploading an image to the Blob table using the UUID from a QR code.

   To create these API calls, select the **OData Integration** type:
   ![](./media/image9.png)

3. Insert the link to the description of our API services (\$metadata) from the API server:

   https://afanasevdm-cfruntime-371tohiy-dev-dbapi-fiori-srv.cfapps.us10.hana.ondemand.com/service/catalog/$metadata
   
   Then click **Verify URL**:
   ![](./media/image10.png)

4. The configurator, using the metadata information, has identified 2 entities: **Request** and **Blobstorage**. Activate both of them:
   ![](./media/image11.png)

5. For these entities, settings for standard access methods (GET, POST, UPDATE, etc.) will appear. Save the configurations by clicking **SAVE DATA RESOURCES**:
   ![](./media/image12.png)

6. As a result, the project will now have access methods defined for the 2 API server entities: **Request** (a table of requests) and **Blobstorage** (a table of blob objects with UUIDs from requests).

   The outcome should look like this:
   ![](./media/image13.png)


# Step 3 «Building the app: connecting to Data»: 

Пройдем во вкладку **DATA**:

![](./media/image8.png)

Далее в секции SAP Build Apps classic data entities создадим определение
2х API вызовов типа OData Integration.

\- Один - API вызов для получения данных о заявке на проход по UUID,
считанного из QR кода.

\- Второй - API вызов для загрузки изображения в Blob таблицу по UUID,
считанного из QR кода.

Для этого выберем **OData Integration** тип:

![](./media/image9.png)

Вставим ссылку описания наших API сервисов (\$metadata) от сервера API:

<https://afanasevdm-cfruntime-371tohiy-dev-dbapi-fiori-srv.cfapps.us10.hana.ondemand.com/service/catalog/$metadata>

нажмем **Verify URL**:

![](./media/image10.png)

Конфигуратор по описанию metadata информации распознал 2 сущности:
**Request, Blobstorage**, активируем обе:

![](./media/image11.png)

Для сущностей появляются элементы настройки стандартных методов доступа
к ним (GET, POST, UPDATE и т.д.). Сохраняем конфигурации нажатием SAVE
DATA RESOURCES:

![](./media/image12.png)

В результате у нас появились в проекте описанные методы доступа к 2
сущностям API сервера: Request (таблица заявок) и Blobstorage (таблица
blob объектов c UUID заявки).

Результат:

![](./media/image13.png)

# Шаг 4 «Архитектура приложения: создание страниц приложения»:

Согласно архитектуре приложения, нужно создать 2 страницы приложения
«Home Page» и "Photo Page". Для этого кликните по ссылке "Home Page":

![](./media/image14.png)

Откроется конфигуратор, где необходимо добавить вторую страницу, кликнув
на **ADD NEW PAGE**:

![](./media/image15.png)

В открывшемся окне введите название страницы «**Photо page**», далее
**OK**:

![](./media/image16.png)

В результате откроется вновь созданная страница, нажмите SAVE:

![](./media/image17.png)

# Шаг 5 «Архитектура приложения: добавление элементов первой странички»:

Переходим на первую страницу приложения, кликнув **Home page** по
навигационной ссылке и потом по самой страничке **Home page**: (может
потребоваться нажать SAVE, если предыдущие изменения не были сохранены)

![](./media/image18.png)

![](./media/image19.png)

Выберите *Headerline* и измените текст на следующий «***Наведите на QR
код заявки в приложении***»:

![](./media/image20.png)

В **LAYOUT** вкладке свойств в разделе **LAYOUT** выберите выравнивание
по центру:

![](./media/image21.png)

и удалите второй **Text 1** элемент:

![](./media/image22.png)

Добавьте элемент **Button** на канву первой странички из библиотеки
элементов слева, вкладка **CORE**. поменяйте название кнопки на ***"Scan
QR"***:

![](./media/image23.png)

# Шаг 6 «Архитектура приложения: добавление логики первой странички»:

Определим переменную **uuid_var** уровня App Variable с типом *"**any
text**"*, куда будет считан UUID заявки, переключив **VIEW --
VARIABLES**:

![](./media/image24.png)

Сохраним изменения через **SAVE**

Перейдем на первую страницу приложения "**Home page**", переключив
**VIEW -- VARIABLES**.

Выберем кнопку **Scan QR**, откроем панель **Add logic to "Button 1"**
внизу экрана:

![](./media/image25.png)

и разместим в открывшейся панели следующие элементы с панели **Logic
CORE** слева:

#### Device: Scan QR/barcode

#### Variables: Set app variable

#### Data: Get Record

#### Navigation: Open page

#### Dialog: Alert

#### Dialog: Alert

И соединим их как показано на рисунке:

![](./media/image26.png)

В логическом блоке **Variables: Set app variable** присвоим переменной
**uuid_var** уровня App Variable считанное и дешифрованное значение из
блока **Scan QR/barcode** привязав значение переменной в поле **Variable
name**:

![](./media/image27.png)

И присвоив значение вывода предыдущего блока, кликнув на иконку под
**Assigned value** и выбрав **Output value of another node**:

![](./media/image28.png)

Далее выбрать **Scan QR/barcode** у Select logic node, **Scan QR/barcode
/ QR barcode content** у Select node output, далее кнопка **SAVE**:

![](./media/image29.png)

Для чтения данных по заявке методом **Get record** используя
дешифрованное значение UUID, хранящееся в переменной **uuid_var**,
заполняем параметры блока следующим образом:

\- API вызов из ресурса **Request**:

![](./media/image30.png)

Id параметр заполняется переменной:

![](./media/image31.png)

Далее **App Variables**, дальше выбираем переменную **uuid_var** и жмем
**SAVE**:

![](./media/image32.png)

Для первого элемента **Alert** задаем текст «**cannot read QR**» вывода
при неудачном чтении QR кода:

![](./media/image33.png)

Для второго **Alert** аналогично задаем сообщение неуспешного чтения из
API -- "**request not found**":

![](./media/image34.png)

Сохраняем все изменения в проекте через кнопку SAVE:

![](./media/image35.png)

# Шаг 7 «Архитектура приложения: добавление переменных и элементов второй странички»:

Переходим на страницу Photo page:

![](./media/image36.png)

Переключитесь в режим **VARIABLES** и добавьте 2 переменные **name** и
**surname** как параметры страницы на вкладке **PAGE PARAMETERS**:

![](./media/image37.png)

Перейдите на вкладку **PAGE VARIABLES** и создайте еще 2 переменные для
хранения сделанной фотографии с соответствующими типами данных (mimetype
-- text; photo_path -- local file system path):

![](./media/image38.png)

Перейдите в режим VIEW и удалите **Headline** элемент. А для текстового
элемента задайте свойство Content в виде формулы со значением
**JOIN(\[\"Сделайте фото для \", params.name, params.surname\], \'
\')**:

![](./media/image39.png)

Сохраните результат

![](./media/image40.png)

Расположите текст по центру, поменяв свойства тестового поля как на
картинке **LAYOUT -\> Text Align -\> center**:

![](./media/image41.png)

Далее добавьте на канву страницы **Photo page** новые элементы:

\- Image

\- Button 1

\- Button 2

И поменяйте label для кнопок как на картинке:

![](./media/image42.png)

Для элемента Image увяжите свойство **Source** картинки с переменной
**PAGE VARIABLE: photo_path**:

![](./media/image43.png)

Далее поменяйте размеры картинки на фиксированные:

![](./media/image44.png)

И расположите картинку по центру:

![](./media/image45.png)

# Шаг 8 «Архитектура приложения: добавление логики работы второй странички -- кнопка take photo»:

Выберем кнопку take a photo и откроем панель добавления логики и кликнем
на **Marketplace**:

![](./media/image46.png)

В поле поиска напишем «covert file to base64» и выберем найденный
элемент:

![](./media/image47.png)

Далее установим компонент нажав **INSTALL**:

![](./media/image48.png)

После этого, элемент появится во вкладке INSTALLED:

![](./media/image49.png)

Далее соберем следующие элементы на канве логики работы кнопки:

DEVICE: take photo

VARIABLES: set page variable

VARIABLES: set page variable

DIALOG: Alert

И свяжем как на картинке:

![](./media/image50.png)

Один элемент присвоения переменной увяжем с **mimeType** вывода элемента
**Take photo** и переменной страницы **mimetype**:

![](./media/image51.png)

И сохранить.

Во втором элементе настроить присвоение страничной переменной
**photo_path** с выводом блока **Take photo -- path**:

![](./media/image52.png)

И сохранить.

Для элемента **DIALOG: Alert** задайте текст "**failed to take photo**":

![](./media/image53.png)

Сохраните проект:

![](./media/image54.png)

# Шаг 9 «Архитектура приложения: добавление логики работы второй странички -- кнопка upload to system»: 

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

![](./media/image55.png)

Далее для элемента **Convert file to base64** зададим след параметры:
URL файла для конверсии укажем из **PAGE VARIABLE photo_path**:

![](./media/image56.png)

Для элемента Create Record выберем resource name: Blobstorage:

![](./media/image57.png)

А для поля **Record** выберем «**Object with properties**» и зададим
след значения:

\- поле **mimetype** увязать с переменной **mimetype** типа **PAGE
VARIABLE**

\- поле **req_uuid** увязать с переменной **uuid_var** типа **APP
VARIABLE**

\- поле **Imagedata** увязать с выводом предыдущего элемента-конвертора
**Convert file to Base64 / Base64 text**

![](./media/image58.png)

Для Alert успешного создание записи в БД выводим сообщение успеха -
***Uploaded***:

![](./media/image59.png)

В случае неуспешной записи в БД выводим сообщение -- ***Failed to
Upload***:

![](./media/image60.png)

В случае неуспешной ковертации изображения выводим сообщение --
***failed to convert***:

![](./media/image61.png)

Сохраняем весть проект:

![](./media/image62.png)

# Шаг 10 «Архитектура приложения: увяжем передачу параметров между страницами»: 

Откроем страницу **Home page** и выберем кнопку **Scan QR**, откроем
панель логики работы кнопки и выберем блок **NAVIGATION: Open page**. В
свойстве page (следующей открываемой страницы) укажем страницу **Photo
page**:

![](./media/image63.png)

А требуемые параметры открываемой страницы (**PAGE PARAMETERS**
определенные для **Photo page** ранее) увяжем с возвращенным результатом
работы **API Get record** к сущности **Request**:

![](./media/image64.png)

И сохранить.

Сохраняем весть проект:

![](./media/image62.png)

# Шаг 11 «Запуск приложения в тестовом режиме на телефоне»:

1.  Устанавливаем приложение **SAP Build Apps** из Appstore или Google
    Store

2.  Переходим на вкладку Launch в проекте приложения, далее **OPEN
    PREVIEW PORTAL**:

![](./media/image65.png)

3.  На моб телефоне заходим в приложение **SAP Build Apps**, выбираем
    вход через SAP Build Apps:

![](./media/image66.png)

4.  Далее 6ти-значный код вводим на портале в браузере и жмем
    **Confirm**:

![](./media/image67.png)

5.  Далее на мобильном приложении в списке Apps находим свой проект и
    жмем **Open**:

![](./media/image68.png)

Приложение запускается

![](./media/image69.png)


6.  Зайдите на портал и откройте **Reception** вкладку:

https://samruktest-gdpazdel.workzone.cfapps.eu10.hana.ondemand.com/site#workzone-home&/home

в списке найдите свою заявку, провалитесь в нее, считайте QR code на мобильном устройстве и сделайте фото

в результате фото появится на приложении ресепшеониста на портале.
