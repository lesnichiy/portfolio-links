# portfolio-links

## Project #1: Momentum

Momentum - аналог [одноимённого приложения](https://chrome.google.com/webstore/detail/momentum/laookkfknpbbblfpciffpaejjkokdgca?hl=ru) интернет-магазина Chrome. Приложение показывает время и имя пользователя, его цель на текущий день. Фоновое изображение меняется в зависимости от времени суток. Для хранения данных приложение использует локальное хранилище - local storage.

### Deploy:
https://rolling-scopes-school.github.io/lesnichiy-JS2020Q3/momentum/

### Функционал

- **Базовая функциональность**
  - время выводится в 24-часовом формате, обновляется каждую секунду 
  - выводится день недели, дата, месяц
  - можно ввести имя пользователя и его цель. Для ввода данных используется клавиша Enter
  - имя пользователя и его цель сохраняются в local storage и отображаются после обновления страницы
  - фоновое изображение и приветствие изменяются в зависимости от времени суток (утро, день, вечер, ночь)
  - при клике в поле ввода текст, который там был, исчезает, если пользователь ничего не ввёл или ввёл пустую строку, текст восстанавливается
- **Смена фонового изображения**
  - фоновые изображения меняются каждый час (в 00 мин) и выбираются в зависимости от времени суток (утро, день, вечер, ночь)
  - есть кнопка, при клике по которой можно пролистать все фоновые изображения за сутки
  - изображения пролистываются в том же порядке, в котором они менялись бы в реальном времени (утро, день, вечер, ночь), начиная с того, которое соотвествует текущему времени суток
  - при обновлении страницы формируется новый список фоновых изображений на текущие сутки
  - при клике по кнопке для обновления фонового изображения происходит плавная смена фоновых изображений, исключена ситуация, когда пользователь видит частично загрузившееся изображение
- **Цитата дня**
  - при загрузке приложения выводится цитата
  - при перезагрузке страницы цитата заменяется на другую
  - есть кнопка, при клике по которой меняется цитата
- **Прогноз погоды**
  - в приложении есть возможность указать город
  - для указанного пользователем города выводится прогноз погоды
  - указанный пользователем город сохраняется в local storage и отображается при обновлении страницы. Также отображается прогноз погоды для него
  - прогноз погоды включает в себя данные о температуре, относительной влажности воздуха, скорости ветра
  - прогноз погоды включает в себя иконку погоды 
  - если пользователь вводит пустую строку, данные не меняются, отображается прежний прогноз погоды. Если пользователь вводит данные, для которых API погоды не возвращает результат, выводится уведомление об ошибке в человекочитаемом формате
- **Адаптивный дизайн**
  - элемены приложения оптимально занимают площадь страницы
  - приложение корректно отображается как на компьютере, так и на мобильных устройствах. Отсутствует горизонтальная полоса прокрутки. Минимальное разрешение экрана, при котором проверяется корректность отображения приложения - 320px

## Project #2: Shelter (HTML/CSS/JS)

Адаптивная вёрстка двух страниц - `Main Page` и `Pets Page` - согласно макета: [**Figmа shelter**](https://www.figma.com/file/RJO7A4D5K1V6FykBuSNIz4/shelter)

Адаптив реализован для трёх диапазонов:
- 1280px <= width
- 768px <= width < 1280px
- 320px <= width < 768px
  - Меню в `Header` становится бургер меню.

### Deploy:
https://rolling-scopes-school.github.io/lesnichiy-JS2020Q3/shelter/pages/main/index.html

### Функционал

#### Main Page

##### Burger menu

- Бургер меню отображается на странице только при width < 768px.
- При нажатии на бургер меню, с правой стороны выезжает блок шириной 320px, в котором находятся вертикально расположенные и центрированные элементы меню.
- При открытии/закрытии присутствует анимация выезда.
- Область, выступающая за 320px, затемнена.
- При открытии/закрытии меню, сама иконка меню поворачивается на 90 градусов и присутствует анимация поворота иконки.
- При открытии меню возможность скролла самой страницы пропадает.
- При нажатии вне границ меню, на затемненную область, или на кнопку с иконкой бургер меню, меню заезжает обратно, а страницу снова можно скроллить.

##### Slider (блок Our Friends)

- Слайдер реализован со стрелками, при нажатии на которые появляется новый блок с карточками.
- Слайдер бесконечный, не имеет границ, т.е. можно нажимать влево и вправо сколько угодно раз, и каждый раз контент в блоках будет новый.
- При 1280px <= width в блоке слайда 3 карточки питомцев. При нажатии на стрелку, все 3 карточки будут заменены на новые.
- При 768px <= width < 1280px в блоке слайда 2 карточки питомцев. При нажатии на стрелку, 2 карточки будут заменены на новые.
- При width < 768px в блоке слайда 1 карточка питомца. При нажатии на стрелку, меняется всего 1 карточка на новую.
----
Каждый новый слайд содержит **псевдослучайный** набор питомцев, т.е. формируется из исходных объектов файла `pets.json` в случайном порядке, но с условиями:
- В текущем блоке слайда карточки с питомцами не повторяются.
- В следующем блоке нет дублирующихся карточек с карточками текущего блока. Например в слайдере из 3 карточек, следующий слайд будет содержать 3 новых карточки питомца, таких, каких не было среди 3х карточек на предыдущем слайде.
----

##### Popup (при клике на карточку в блоке Our Friends)

- При нажатии на любое место карточки (блока) с описанием конкретного питомца появляется попап, его контент без учета крестика в правом верхнем углу центрируется по ширине и высоте экрана. Остальная часть страницы затемняется.
- При появлении попапа возможность скролла самой страницы пропадает.
- При нажатии на окно (блок) попапа ничего не происходит.
- При нажатии вне границ попапа, на затемненную область, или на кнопку с крестиком, попап и затемнение исчезают, а страницу снова можно скроллить.
- При наведении мышкой на затемненную область или кнопку с крестиком, т.е. при событии `hover`, кнопка получает эффект наведения. При этом при наведении на окно (блок) самого попапа ничего не происходит.
- При 768px <= width в дизайне попапа есть картинка питомца.
- При width < 768px в дизайне попапа картинки питомца нет.
  
#### Pets Page

##### Burger menu

Функционал аналогичен странице `Main Page`.

##### Popup

Функционал аналогичен странице `Main Page`.

##### Pagination
----
Каждая новая страница пагинации содержит **псевдослучайный** набор питомцев, т.е. формируется из исходных объектов файла `pets.json` в случайном порядке, но с условиями:
- При загрузке `Our Pets` формируется массив из 48 объектов питомцев. В данном массиве каждые 8, каждые 6, и каждые 3, карточки питомцев не повторяются. Т.е. на одной странице пагинации не может быть одноврменно две одинаковых карточки питомца.
- При каждой загрузке набор карточек, отображенных на странице пагинации, формируется случайно.
- При неизменных размерах области пагинации, в том числе размерах окна браузера, возвращаясь на страницу под определнным номером, контент на ней всегда будет одинаков. Т.е. карточки питомцев будут в том же расположении, что и были до перехода на другие страницы.
- При 1280px <= width на странице одновременно показаны 8 неповторяющихся карточек питомцев.
- При 768px <= width < 1280px на странице одновременно показаны 6 неповторяющихся карточек питомцев.
- При width < 768px на странице одновременно показаны 3 неповторяющихся карточки питомцев.
----
- При переключении страниц данные меняются. 
- При каждой загрузке или перезагрузке `Our Pets` в браузере всегда активной является первая страница.
- Кнопка `<<` всегда открывает первую страницу
- Кнопка `<` открывает предыдущую до текущей страницы
- Кнопка `>` открывает следующую после текущей страницы
- Кнопка `>>` всегда открывает последнюю страницу
- В кружке по центру указан номер текущей страницы
- При открытии первой страницы, кнопки `<<` и `<` - неактивны.
- При открытии последней страницы, кнопки `>` и `>>` - неактивны.
- Всего для пагинации сгенерировано 48 объектов питомцев.
- При 1280px <= width на странице одновременно показаны 8 карточек питомцев.
- При 768px <= width < 1280px на странице одновременно показаны 6 карточек питомцев.
- При width < 768px на странице одновременно показаны 3 карточки питомцев.

## Project #3: Virtual Keyboard

Проект по созданию виртуальной клавиатуры.

### Deploy:
https://rolling-scopes-school.github.io/lesnichiy-JS2020Q3/virtual-keyboard/

***Внимание!*** По умолчанию озвучивание нажатия клавиш включено. Будьте наготове.

### Функционал
- **Базовая функциональность**
  - При клике мышкой по клавишам с символами, эти символы отображаются в окне ввода.
  - Есть клавиша CapsLock, переводящая все буквы в верхний регистр, клавиша пробел, клавиша Backspace, удаляющая символы перед курсором, клавиша Enter для перехода на новую строку.
  - Клавиатуру можно скрыть и отобразить на экране.
  - В окне для ввода текста сохраняются все возможности обычной физической клавиатуры: текст можно набирать, выделять, удалять, добавлять текст в средину строки и т.д.
- **Клавиша Shift**
  - Клавиша Shift работает как в обычной клавиатуре - меняет регистр букв, выводит дополнительные символы вместо цифр и символов основной раскладки.
  - Переключение клавиши Shift происходит по клику, при этом меняется состояние клавиши (активная-неактивная), на клавиатуре отображаются соответствующие символы. 
- **Смена языка en/ru** 
  - Для смены языка добавлена дополнительная клавиша en/ru, при клике по которой происходит переключение между русской и английской раскладкой клавиатуры.
  - При переключении языка на клавише en/ru отображается установленный в данный момент язык, на других клавишах клавиатуры отображаются символы выбранного языка.
- **Горизонтальные стрелки для перемещения в пределах строки** 
  - Для перемещения в пределах строки добавлены стрелки влево-вправо, клики по которым реализуют горизонтальную навигацию позиции курсора.
  - После перемещения позиции курсора ввод/удаление текста происходит по позиции курсора в т.ч. внутри строки.
- **Дополнительная функциональность**
  - Подсветка (изменение стиля клавиши при клике) клавиш виртуальной клавиатуры при кликах по клавишам физической клавиатуры.
  - Озвучивание нажатия клавиш виртуальной клавиатуры (звуки при печати в русской и английской раскладке отличаются, для функциональных клавиш предусмотрены уникальные звуки, не зависящие от раскладки).
  - Есть возможность включить и отключить озвучивание нажатия клавиш, для этого на виртуальной клавиатуре предусмотрена отдельная клавиша.
  - Клавиатура адаптируется под размер страницы.
- **Возможность голосового ввода текста** (SpeechRecognition, работает в Google Chrome):
  - На виртуальной клавиатуре есть отдельная клавиша, при клике по которой можно включить/отключить голосовой ввод текста.
  - Язык распознавания голоса en/ru будет таким, который был активен при нажатии кнопки голосового ввода (для смены языка распознования: отключаем голосовой ввод, переключаем язык, включаем голосовой ввод)
