# web_developer_6_Building_Interactive_JavaScript_Websites

# 6. Building Interactive JavaScript Websites

## JavaScript Interactive Websites

### JavaScript и HTML
HTML определяет структуру веб-страницы, используя элементы страницы в качестве строительных блоков. Тем не менее, HTML сам по себе не может обеспечить интерактивность веб-страницы, вот где JavaScript.

В веб-разработке CSS обеспечивает стиль для нашей структуры HTML. 

Если HTML и CSS обеспечивают структуру и стиль в этой аналогии, JavaScript обеспечивает интерактивность, позволяя нашей фигурке двигаться.

Веб-программисты используют JavaScript, чтобы сделать веб-страницы динамичными и интерактивными. Этот мощный язык сценариев инкапсулирован в свой собственный элемент HTML: <script>элемент. Вы можете думать об этом <script>элементе как о двери в JavaScript для HTML. 
  
### Тег script
Элемент позволяет добавить код JavaScript внутри HTML - файла. 

```
<h1>This is an embedded JS example</h1>
<script>
  function Hello() {
    alert ('Hello World');
  }
</script>
```

### The src attribute
Связывание кода является предпочтительным из-за концепции программирования, называемой разделением проблем (SoC). Вместо того, чтобы иметь грязный код, который находится в одном и том же файле, веб-разработчики разделяют свой код на разные файлы, что облегчает понимание каждой «проблемы» и делает ее более удобной при внесении изменений.

Для этого упражнения вместо написания JavaScript в нашем HTML-файле мы запишем его в своем собственном файле, а затем свяжем этот код с именем пути к файлу . Мы сделаем это, используя атрибут, который может пробудить вашу память: srcатрибут!

```
<script src="./exampleScript.js"></script>
```
### How are scripts loaded?
<script>элемент позволяет файлам HTML загружать и выполнять JavaScript. JavaScript может быть встроен в <script>тег или тег script может ссылаться на внешний файл. Прежде чем мы углубимся, давайте немного поговорим о том, как браузеры анализируют HTML-файлы на веб-страницах. Это информирует, где включить <script>элемент в ваш HTML-файл.
  
Браузеры оснащены HTML-парсерами, которые помогают браузерам отображать элементы соответствующим образом. Элементы, включая <script>элемент, по умолчанию анализируются в порядке их появления в файле HTML. Когда анализатор HTML встречает <script>элемент, он загружает скрипт, затем выполняет его содержимое перед анализом остальной части HTML.
  
### Defer attribute
Когда анализатор HTML сталкивается с <script>элементом, он останавливает загрузку его содержимого. После загрузки выполняется код JavaScript, и анализатор HTML переходит к анализу следующего элемента в файле. Это может привести к медленному времени загрузки вашего сайта. HTML4 ввел атрибуты defer и async <script>элемента для адресации времени ожидания пользователя на веб-сайте в зависимости от различных сценариев.
  
В атрибуте Defer указывает сценарии должны выполняться после того, как файл HTML полностью разобран. Когда анализатор HTML встречает <script>элемент с deferатрибутом, он загружает сценарий, но откладывает фактическое выполнение JavaScript до тех пор, пока не завершит анализ остальных элементов в файле HTML.
```
<script src="example.js" defer></script> 
```  
Когда сценарий содержит функциональность, которая требует взаимодействия с DOM, deferатрибут является подходящим способом. Таким образом, он гарантирует, что весь HTML-файл был проанализирован перед выполнением скрипта

### Async attribute
В asyncнагрузках атрибутов и выполняет скрипт асинхронно с остальной частью веб - страницы. Это означает, что, подобно defer атрибуту, анализатор HTML продолжит синтаксический анализ остальной части HTML, когда сценарий загружается в фоновом режиме. Однако с этим asyncатрибутом сценарий не будет ожидать анализа всей страницы: он будет выполнен сразу после загрузки.
```
<script src="example.js" async></script>
```
async полезно для сценариев, которые независимы от других сценариев, чтобы функционировать соответственно. Таким образом, если не имеет значения, в какой именно момент выполняется файл сценария, наиболее подходящим вариантом является асинхронная загрузка, поскольку она оптимизирует время загрузки веб-страницы.

https://youtu.be/iwNUJU5D3aI

## THE DOCUMENT OBJECT MODEL
### What is the DOM?

Объектная модель документа , сокращенно DOM, является мощным древовидная структура , которая позволяет программистам иерархии концептуализации и доступ к элементам на веб - странице.

DOM - это одно из сокращений в области веб-разработки. На самом деле, полезный способ понять, что делает DOM, - разбить аббревиатуру, но не по порядку:

DOM является логическим древовидной M Одел , который организует веб - страницу HTML D ocument как O ▪ Таблица.

DOM - это независимая от языка структура, реализованная браузерами, чтобы позволить языкам веб-сценариев, таким как JavaScript, организованно получать, изменять и обновлять структуру веб-страницы HTML.

По этой причине нам нравится думать о DOM как о связи между веб-страницей HTML и языками сценариев.

### The DOM as a Tree Structure
Древовидное моделирование используется во многих областях, включая эволюционную науку и анализ данных. Возможно, вы уже знакомы с концепцией генеалогических деревьев: эти диаграммы представляют семейные отношения между потомками данной фамилии.

Дерево DOM следует логике, аналогичной логике семейного дерева. Семейное древо состоит из членов семьи и их отношений с фамилией. В информатике мы бы назвали каждого члена семьи узлом.

Мы определяем узел как точку пересечения в дереве, которое содержит данные.

В дереве DOM самый верхний узел называется корневым узлом и представляет документ HTML. Потомки корневого узла являются HTML - теги в документе, начиная с <html>тега следуют <head>и <body>теги и так далее.
  
### Parent Child Relationships in the DOM
Следуя метафоре родословной, давайте определим некоторую ключевую терминологию в иерархии DOM:

Родительский узел является ближайшим узлом подключенного к другому узлу в направлении к корню.

Дочерний узел является ближайшим узлом подключенного к другому узлу в направлении от корня.

Знание этих терминов позволит вам понять и обсудить DOM как древовидную структуру. Фактически вы также увидите, что эта терминология используется при обращении к структуре вложенности HTML-кода. Программисты ссылаются на элементы, вложенные в другие элементы, как дочерние элементы и родительские элементы соответственно.

### Nodes and Elements in the DOM
Как уже упоминалось, узел является эквивалентом каждого члена семьи в семейном древе. Узел - это точка пересечения в дереве, которое также содержит данные.

В дереве DOM есть девять различных типов объектов узлов. На нашей диаграмме объекты узлов с прямоугольниками с острыми краями имеют тип Element , а прямоугольники с закругленными краями имеют тип Text , поскольку они представляют текст внутри элементов абзаца HTML.

При попытке изменить веб-страницу сценарий будет в основном взаимодействовать с узлами DOM элемента типа. Элементы являются строительными единицами веб-страниц HTML, они содержат все между открывающим тегом и закрывающим тегом. Если тег является самозакрывающимся тегом, то это сам элемент.

### Attributes of Element Node
Узлы элементов DOM моделируют элементы в документе HTML.

Так же, как к элементу HTML - страницы, DOM позволяет нам доступ к атрибутам Узла, такие , как его class, idи инлайн style.


## JavaScript and DOM

### The document keyword
Объектная модель документа , сокращенно DOM, является мощным древовидная структура , которая организует элементы на веб - странице и позволяет скриптовых языков для доступа к ним. Этот урок будет посвящен некоторым наиболее полезным методам и свойствам интерфейса DOM в JavaScript. Этот интерфейс реализован каждым современным браузером.

Перво-наперво! documentОбъект в JavaScript является дверью в структуру DOM. documentПозволяет получить доступ к корневому узлу дерева DOM. Прежде чем вы сможете получить доступ к определенному элементу на странице, сначала вы должны получить доступ к самой структуре документа. documentПозволяет сценарии для детей доступа к DOM в качестве свойств.

Например, если вы хотите получить доступ к <body>элементу в вашем скрипте, вы можете получить к нему доступ как к свойству document, набрав document.body. Это свойство вернет элемент тела этого DOM.

Точно так же вы можете получить доступ к <title>элементу со .titleсвойством. Смотрите полный список всех documentсвойств.
  
### Tweak an Element
При использовании DOM в вашем скрипте для доступа к элементу HTML у вас также есть доступ ко всем свойствам этого элемента.

Это включает в себя возможность изменять содержимое элемента, а также его атрибуты и свойства, которые могут варьироваться от изменения текста внутри pэлемента до назначения нового цвета фона a div.

Вы можете получить доступ и установить содержимое элемента с помощью .innerHTMLсвойства.
```
document.body.innerHTML = 'The cat loves the dog.';
```
.innerHTMLСвойство может также добавить любой допустимый HTML, в том числе должным образом отформатированных элементов. В следующем примере h2элемент присваивается в качестве дочернего <body>элемента:

### Select and Modify Elements
Что если мы хотим выбрать конкретный элемент? Интерфейс DOM позволяет нам получить доступ к определенному элементу с помощью селекторов CSS. Селекторы CSS определяют элементы, к которым применяется набор правил CSS, но мы также можем использовать эти же селекторы для доступа к элементам DOM с помощью нашего скрипта! Селекторы могут включать имя тега, класс или идентификатор.

.querySelector() Метод позволяет определить селектор CSS , а затем возвращает первый элемент , который соответствует этой селектору.
```
document.querySelector('p');
```
Вы также можете использовать другие селекторы CSS, такие как .класс элемента или его #идентификатор.

Другой вариант, если вы хотите получить доступ к элементам напрямую по их элементам id, вы можете использовать метко названную .getElementByID()функцию
```
document.getElementById('bio').innerHTML = 'The description';
```

### Style an element
Другой способ изменить элемент - изменить его стиль CSS. .styleСвойство DOM элемента обеспечивает доступ к встроенному стилю этого HTML - тег.

Синтаксис соответствует element.style.propertyформату с propertyпредставлением свойства CSS.

Например, следующий код выбирает первый элемент со значком classof blueи назначает синий цвет как background-color:
```
let blueElement = document.querySelector('.blue');
blueElement.style.backgroundColor = 'blue';
```
В отличие от CSS, свойство стиля DOM не реализует такие дефисы, как background-color, а скорее, обозначение верблюжьих букв backgroundColor.
```
document.querySelector('.blue').style.fontFamily = 'Roboto';
```

### Create and Insert Elements
Так же, как DOM позволяет сценариям изменять существующие элементы, он также позволяет создавать новые.

.createElement(tagName)Метод создает новый элемент на основе указанного имени тега , переданное в него в качестве аргумента. Тем не менее, он не добавляет его к документу. Создает пустой элемент без внутреннего HTML.

Чтобы создать элемент и добавить его на веб-страницу, необходимо назначить его дочерним по отношению к элементу, который уже существует в DOM. Мы называем этот процесс добавлением. .appendChild()Метод будет добавить дочерний элемент в качестве последнего дочернего узла.
```
let paragraph = document.createElement('p');

paragraph.id = 'info'; 

paragraph.innerHTML = 'The text inside the paragraph';

document.body.appendChild(paragraph);
```
В отличие от .innerHTMLсвойства, в этом случае .appendChild()метод не заменяет содержимое внутри родительского объекта body. Скорее, он добавляет элемент в качестве последнего потомка этого родителя

### Remove an Element
В дополнение к изменению или созданию элемента с нуля, DOM также позволяет удалить элемент. .removeChild()Метод удаляет заданный ребенка от одного из родителей.
```
let paragraph = document.querySelector('p');
document.body.removeChild(paragraph);
```
Если вы хотите скрыть элемент, поскольку его не нужно загружать изначально, .hiddenсвойство позволяет скрыть его, назначив его как true или false:
```
document.getElementById('sign').hidden = true;
```
Приведенный выше код не удалял элемент из DOM, а скрывал его. Это не то же самое, что установка свойства видимости CSS на скрытый. Чтобы получить список лучших вариантов использования этого свойства, прочитайте список в документации MDN .

### Interactivity with onclick
Вы можете добавить интерактивность к элементам DOM, назначив функцию для запуска на основе события .

События могут включать в себя все, что угодно, от клика до пользователя, наведенного на элемент.

.onclickСвойство позволяет назначить функцию для запуска на событие щелчка на элементе:
```
let element = document.getElementById('interact');
element.onclick = function() { element.style.backgroundColor = 'blue' };
```

### Traversing the DOM
В иерархии DOM родительские и дочерние отношения определяются в зависимости от положения корневого узла.

Родительский узел является ближайшим узлом подключенного к другому узлу в направлении к корню.

Дочерний узел является ближайшим узлом подключенного к другому узлу в направлении от корня.

Эти отношения следуют структуре вложенности, присутствующей в коде HTML. Элементы, вложенные в один тег HTML, являются дочерними элементами этого родительского элемента.

Каждый узел элемента DOM имеет свойство .parentNodeand .children. Свойство вернет список дочерних элементов и вернется, nullесли у элемента нет дочерних элементов.

.firstChild Имущество будет предоставлять доступ к первому дочернему этому родительскому элементу.

