.. highlight:: cpp

Среды разработки (IDE)
----------------------

Для C++ есть довольно много сред разработки (IDE) — программ-редакторов, в которых вы собственно будете набирать код и из которых вы будете запускать программы.
Наиболее распространены на олимпиадах три среды — Code::Blocks, Microsoft Visual Studio и CLion.
Я ниже вкратце опишу Code::Blocks и Visual Studio, потому что первая бесплатна, а у второй есть бесплатная версия.
У CLion нет общедоступной бесплатной версии, поэтому про него писать я не буду. Кроме того, в контексте обучения школьников 
я иногда встречаю упоминания среды Dev-C++. Но она очень старая, и используется очень редко;
в частности, на серьезных олимпиадах я ее, кажется, не встречал, поэтому не надо ее использовать.

В целом, для самого начала я рекомендую использовать Code::Blocks; но также стоит достаточно рано освоить и Visual Studio,
хотя бы потому, что бывают олимпиады, где вам предоставляют только ее.

Тем, кто занимается в `моем курсе <https://algoprog.ru>`_: если у вас возникают какие-либо проблемы
с IDE, обязательно пишите мне. Я вполне допускаю, что описания IDE ниже может быть недостаточно для того,
чтобы в них сразу разобраться.

Code::Blocks
~~~~~~~~~~~~

Это бесплатная кроссплатформенная среда разработки. Ее можно скачать с официального сайта http://codeblocks.org,
а именно
`полный установщик под Windows, включая компилятор GCC <https://www.fosshub.com/Code-Blocks.html?dwl=codeblocks-20.03mingw-setup.exe>`_,
или `другие варианты установки, в том числе под другие ОС <http://codeblocks.org/downloads/26>`_.

Это достаточно простая IDE без особых заморочек, очень напоминает простые IDE из других языков программирования, 
типа Wing IDE для питона и встроенной IDE для Pascal ABC. Все просто: создаете новый файл, пишете код, запускаете 
кнопкой с зеленой стрелочкой (точнее, кнопкой с шестеренкой и зеленой стрелочкой, потому что вам обычно надо скомпилировать, 
и только потом запускать код). Все достаточно очевидно, и вряд ли тут требуются дополнительные разъяснения.

При этом после запуска и завершения программы Сode::Blocks задерживает окошко программы на экране, 
чтобы вы смогли посмотреть, что вывела ваша программа. В разных других руководствах по C++ вам могут предлагать 
использовать специальные конструкции типа ``system("pause")`` или ``getch``,
чтобы задержать выполнение программы на экране — не надо этого делать, Code::Blocks сам вам задержит программу.

Кроме того, у Code::Blocks есть две неочевидных особенности. 
Во-первых, когда вы сохраняете программу в первый раз, надо явно указать расширение файла ``.cpp``
(т.е. в диалоге сохранения файла написать не ``my_best_program``, а ``my_best_program.cpp``), 
иначе по умолчанию программа сохранится как ``.c`` и соответственно компилятор будет считать, 
что это программа на C, а не на C++.

Во-вторых, не так просто сделать, чтобы заработал дебаггер (хотя поначалу вам это и не надо). 
Для этого, во-первых, надо, чтобы дебаггер был установлен на компьютере (Code::Blocks использует компилятор gcc и дебаггер gdb, надо, 
чтобы они были установлены; установщик, указанный выше, скорее всего их устанавливает), 
во-вторых, просто файлы, созданные по кнопке «New», Code::Blocks не будет отлаживать. 
Чтобы дебаггер заработал, надо в Code::Blocks создать «проект», и уже в «проект» добавить 
файл с исходным кодом (существующий или новый). Но это достаточно просто и прямолинейно.

Microsoft Visual Studio
~~~~~~~~~~~~~~~~~~~~~~~

(Не путайте с Visual Studio Code — это две совсем разных IDE.)

Это заметно более продвинутая, профессиональная, IDE. В полном варианте она платная, но есть вариант Visual Studio Community, 
который можно `скачать бесплатно с официального сайта Microsoft <https://visualstudio.microsoft.com/ru/vs/community/>`_.
(Ранее эта версия называлась Visual Studio Express.)

Она уже не такая простая, как Code::Blocks, в ней вы не можете просто так создать новый файл, в ней надо создавать «проект». 
Но в первом приближении это достаточно просто: через File — New project, дальше в диалоге выбираете тип проекта (про это см. ниже),
указываете, куда его сохранить, и т.д. При этом в Visual Studio есть еще понятие *solution* — это группа связанных проектов, —
и поэтому при создании проекта будет несколько пунктов про solution.
Поначалу не так существенно, как отвечать на вопросы про solution — вы можете создавать отдельный solution
на каждую свою программу, можете сделать один solution и добавлять в него проекты, и т.п.

После создания проекта далее все тоже уже достаточно прямолинейно: пишете код, на панели инструментов есть кнопка с зеленой стрелкой,
она запускает программу (хотя лучше запускать через горячие клавиши F5 или Ctrl-F5, см. далее), и т.д.

Но тут есть две проблемы-особенности.

Во-первых, если вы просто так создадите проект, то студия не будет задерживать окошко программы на экране после завершения программы. 
Если вы хотите посмотреть, что ваша программа вывела на экран, вам надо будет добавлять в конец программы какую-нибудь 
задержку типа ``system("pause")`` или ``getch``. А это очень плохо, в частности, не все тестирующие системы хорошо к этому 
относятся (еще бы — вашей программе уже пора заканчивать работу, а она никак не завершается),
ну и вообще это очень плохая практика. Поэтому так делать не надо.

Вторая проблема — по умолчанию студия создает проект с включенными так называемыми pre-compiled headers, 
и в начале кода появляется строчка ``#include "pch.h"``. Нам это не нужно, это только мешает, 
потому что код с такой строчкой не будет компилироваться в тестирующей системе, а без нее 
не будет компилироваться у вас локально в студии.

Обе проблемы решаются правильным созданием проекта. А именно, при создании проекта надо явно убедиться, 
что вы указали два параметра для проекта: во-первых, это должно быть console application 
(это повлияет на задержку программы, см. ниже), во-вторых, это должно быть empty project (а это повлияет на pch). 

Как это сделать, зависит от версии Visual Studio (я выше писал только про VS Community, но вы можете встретиться,
особенно на олимпиадах или в школе/университете, и с другими версиями). В старых версиях в окошке создания 
проекта надо было выбрать тип проекта а-ля Console application, и уже далее в следующем окошке поставить галочку Empty 
project. В последних версиях надо выбрать тип проекта «Windows Desktop Wizard», по-русски «Мастер классических приложений Windows» 
(не «пустой проект», не «консольное приложение», а именно «wizard»/«мастер», его всегда непросто найти), 
и в следующем окошке в выпадающем меню выбрать Console application и поставить галочку Empty project.

Это может быть не так просто, но повторю еще раз: главное — явно указать Console Application, и явно указать Empty Project.
Если вы первый раз работаете в незнакомой версии, потратьте несколько минут и найдите, как это сделать.

Так вы создадите полностью пустой проект, в котором даже не будет файла, в который надо писать код. 
После этого через меню Project — Add new items добавляете новый .cpp-файл (или там же рядом 
можно добавить уже существующий cpp-файл), и дальше все понятно. После этого студия будет делать 
задержку после запуска программы, при условии, что вы ее правильным образом запускаете 
(я не помню точно — надо запускать программу то ли в режиме отладки, 
то ли наоборот без нее, т.е. то ли F5, то ли Ctrl-F5; попробуйте по-разному и разберитесь), ну и pch не будет.

Параметры компиляции и компиляция из командной строки
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Вообще, конечно, IDE (что Code::Blocks, что Visual Studio) — это просто удобная программа для написания кода
и запуска компилятора и потом полученной программы. Сам компилятор живет более-менее отдельно 
от IDE, и соответственно, если надо, вы его можете запускать вручную (как правило, через командную строку);
собственно, тестирующие системы так и поступают.
Поначалу вам будет удобнее компилировать через IDE, но со временем вам, скорее всего,
в определенных случаях придется компилировать и из командной строки.

Конкретно как компилировать из командной строки, я тут описывать не буду,
вам пока это не нужно. Но важно понимать, что компиляторы C++ позволяет задать 
очень много параметров компиляции — в том числе,
они позволяют указать стандарт C++, с которым вы хотите компилировать программу,
размер стека (про это еще см. ниже), уровень оптимизации (насколько
сильно надо вашу программу оптимизировать), ну и много других параметров.
При компиляции из командной строки вы указываете все эти параметры в командной строке.
Если же вы компилируете из IDE, то параметры компилятора как правило можно указать где-то в настройках IDE.
Изучите это заранее; как минимум, найдите, где в Code::Blocks в настройках компиляции
указывать требуемый стандарт C++, размер стека и уровень оптимизации
(в Visual Studio с этим несколько сложнее).
