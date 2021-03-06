# Розгортання!

> **Зауваження** Цей розділ інколи може бути дещо складним для освоєння. Наполегливо продовжуйте і дійдіть до кінця; розгортання -- важлива частина процесу розробки веб-сайту. Цей розділ розташований посередині посібника, щоб ваш наставник зміг допомогти із дещо хитрим процесом випуску веб-сайту в Інтернет. Це означає, що ви все ще можете завершити цей курс самостійно, якщо раптом не встигаєте. 

До цього часу ваш веб-сайт був доступний лише локально на вашому комп'ютері, тепер ви дізнаєте як його розгорнути! Розгортання -- це процес публікації вашого додатку в Інтернеті таким чином, що люди можуть зрештою зайти і побачити його :).

Як ви вже знаєте, веб-сайт має бути розміщений на сервері. В інтернеті є багато компаній які пропонують такі послуги. Ми будемо використовувати той, який має відносно простий розгортання процес: [PythonAnywhere][1]. PythonAnywhere безкоштовний для малих додатків, в яких не дуже багато користувачів, тож нам цього точно буде достатньо.

 [1]: http://pythonanywhere.com/

Інший зовнішній інструмент, який ми будемо використовувати - це [GitHub][2], платформа для розміщення коду. У нього є альтернативи, але майже кожен програміст зараз має GitHub профіль, і скоро ви будете серед них!

 [2]: http://www.github.com

Ми використаємо GitHub як крок, щоб перенести наш код в та з PythonAnywhere.

# Git

Git - це "система контролю версій", яка використовується багатьма розробниками. Ця програма дозволяє відслідковувати зміни до файлів з часом так, що ви можете повернутись до певних версій пізніше. Схоже на функцію "слідкувати за змінами" в Microsoft Word, але набагато потужніше.

## Встановлення Git

> **Примітка** Якщо ви вже виконали процес встановлення, немає потреби робити це ще раз, - можете перейти до натупного кроку і почати створення свого Git репозиторію.

{% include "deploy/install_git.md" %}

## Створення свого Git репозиторію

Git відслідковує зміни певних файлів в репозиторії коду (коротко – "репо"). Давайте створимо "репо" для нашого проекту. Відкрийте вашу консоль та запустіть наступні команди в папці `djangogirls`:

> **Примітка** Перевірте поточну директорію за допомогою команд `pwd` (OSX/Linux) або `cd` (Windows) перед стартом репозиторію. Ви маєте бути в папці `djangogirls`.

    $ git init
    Initialized empty Git repository in ~/djangogirls/.git/
    $ git config --global user.name "Your Name"
    $ git config --global user.email you@example.com
    

Створення git-репозиторію відбувається тільки один раз на кожен проект (і тобі більше не потрібно буде заново вводити ім'я чи електронну пошту).

Git стежитиме за змінам у всіх файлах у цій директорії, але є певні файли які ми хочемо ігнорувати. Ми зробимо це шляхом створення файлу з назвою `.gitignore` в базової директорії. Відкрий свій редактор і створити новий файл з наступним змістом:

    *.pyc
    __pycache__
    myvenv
    db.sqlite3
    .DS_Store
    

І збережи його як `.gitignore` в базовій директорії "djangogirls".

> **Примітка** Крапка на початку імені файлу важлива! У разі виникнення будь-яких труднощів при створенні (наприклад Mac не любить коли створюють файли, імена яких починаються з крапки через Finder), тоді використати "Зберегти як" у редакторі, це повинно спрацювати.

Перед тим як виконати команду `git add` (також, коли ви просто не впевненні що змінилось) непоганою ідеєю буде виконати `git status`. Це допоможе уникнути сюрпризів, наприклад, додавання чи коміту небажаного файлу. Команда `git status` повертає інформацію про файли у вашому репозиторії: untracked (не додані до репозиторію файли), modified (змінені файли), staged (файл додані до коміту), статус поточної гілки і багато іншого. Вивід повинен бути схожий на:

    $ git status
    On branch master
    
    Initial commit
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    
            .gitignore
            blog/
            manage.py
            mysite/
    
    nothing added to commit but untracked files present (use "git add" to track)
    

Зрештою, зберігаємо наші зміни. Перейдіть до консолі і виконайте наступні команди:

    $ git add -A .
    $ git commit -m "My Django Girls app, first commit"
     [...]
     13 files changed, 200 insertions(+)
     create mode 100644 .gitignore
     [...]
     create mode 100644 mysite/wsgi.py
    

## Викладемо наш код на GitHub

Відкриємо [GitHub.com][2] і створимо новий безкоштовний обліковий запис. (Ті хто зробили це ще на етапі підготовки - справжні молодці!)

Створимо новий репозиторій з назвою "my-first-blog". Залишимо опцію "initialise with a README" не вибраною, .gitignore порожньою (пізніше ми додамо це вручну) і License також залишимо як None.

![][3]

 [3]: images/new_github_repo.png

> **Примітка** Ім'я `my-first-blog` важливе - ви можете вибрати щось інше, але воно буде використовуватись багато разів в інструкціях нижче, і потрібно буде замінити його кожного разу. Мабуть легше просто його залишити як `my-first-blog`.

В наступному екрані ми побачимо посилання для клонування репозиторію - clone URL, скопіюємо його і вставимо у термінал:

![][4]

 [4]: images/github_get_repo_url_screenshot.png

Зараз нам потрібно під'єднати Git репозиторій на локальному комп'ютері до щойно створеного на GitHib.

Введіть у вашій консолі (замінивши `<твоє-github-ім'я>` іменем користувача, вказаним під час створення облікового запису GitHub, але без кутових дужок):

    $ git remote add origin https://github.com/<твоє-github-ім'я>/my-first-blog.git
    $ git push -u origin master
    

Введемо наше ім'я користувача на Github та пароль, і ми побачимо щось на зразок:

    Username for 'https://github.com': hjwp
    Password for 'https://hjwp@github.com':
    Counting objects: 6, done.
    Writing objects: 100% (6/6), 200 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To https://github.com/hjwp/my-first-blog.git
     * [new branch]      master -> master
    Branch master set up to track remote branch master from origin.
    

<!--TODO: maybe do ssh keys installs in install party, and point ppl who dont have it to an extention -->

Наш код тепер на GitHub. Ходімо перевіримо! Виявляється він у хорошій компанії - [Django][5], [Цей майстер клас][6] і багато інших чудових проектів з відкритим кодом також публікують свій код GitHub :)

 [5]: https://github.com/django/django
 [6]: https://github.com/DjangoGirls/tutorial

# Налаштування нашого блогу на PythonAnywhere

> **Примітка** Можливо ви вже створили обліковий запис на PythonAnywhere під час підготовки - якщо це так, немає необхідності робити це знову.

{% include "deploy/signup_pythonanywhere.md" %}

## Завантажимо наш код на PythonAnywhere

Після входу до PythonAnywhere, ми опинимось на головній панелі або сторінці "Consoles". Виберемо опцію почати нову "bash" консоль (Start a new console - bash) - це PythonAnywhere версія консолі, схожа на ту що на вашому комп'ютері.

> **Примітка** PythonAnywhere побудований на основі Linux, тому, якщо ви на Windows, консоль буде трохи відрізнятись від тієї, що на вашому комп'ютері.

Давайте завантажимо наш код з GitHub у PythonAnywhere клонувавши наш репозиторій. Наберіть наступне у консолі на PythonAnywhere (не забудьте використовувати ім'я користувача GitHub замість `< ваше-github-ім'я>`):

    $ git clone https://github.com/<ваше-github-ім'я>/my-first-blog.git
    

Ця команда завантажить копію вашого коду на PythonAnywhere. Давайте перевіримо ввівши `tree my-first-blog`:

    $ tree my-first-blog
    my-first-blog/
    ├── blog
    │   ├── __init__.py
    │   ├── admin.py
    │   ├── migrations
    │   │   ├── 0001_initial.py
    │   │   └── __init__.py
    │   ├── models.py
    │   ├── tests.py
    │   └── views.py
    ├── manage.py
    └── mysite
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py
    

### Створення virtualenv на PythonAnywhere

Так само як і на власному комп'ютері, створіть virtualenv на PythonAnywhere. У консолі Bash введіть:

    $ cd my-first-blog
    
    $ virtualenv --python=python3.4 myvenv
    Running virtualenv with interpreter /usr/bin/python3.4
    [...]
    Installing setuptools, pip...done.
    
    $ source myvenv/bin/activate
    
    (mvenv) $  pip install django whitenoise
    Collecting django
    [...]
    Successfully installed django-1.8.2 whitenoise-2.0
    

> **Примітка** Крок `pip install` може зайняти кілька хвилин. Терпіння і ще раз терпіння! Але якщо він займає більш ніж за 5 хвилин, щось пішло шкереберть. Попросіть допомоги вашого тренера.

<!--TODO: think about using requirements.txt instead of pip install.-->

### Збирання статичних файлів.

Можливо ви поцікавились, що за штука це "whitenoise"? Це інструмент для обслуговування так званих "статичних файлів". Статичні файли це файли які зазвичай не змінюються і не виконують ніякого коду, наприклад HTML чи CSS файли. На серверах вони працюють інакше, ніж на вашому локальному комп'ютері, щоб сервер міг їх подавати нам потрібен спеціальний інструмент, такий як "whitenoise".

Пізніше, коли ми змінимо CSS для нашого сайту, ми дізнаємось трохи більше про статичні файли.

Поки що нам просто потрібно виконати додаткову команду `collectstatic` на сервері. Ця команда каже Django про усі статичні файли які йому потрібні на сервері. На даний момент це в основному файли, що допомагають зробити красивою сторінку адміністрування.

    (mvenv) $ python manage.py collectstatic
    
    You have requested to collect static files at the destination
    location as specified in your settings:
    
        /home/edith/my-first-blog/static
    
    This will overwrite existing files!
    Are you sure you want to do this?
    
    Type 'yes' to continue, or 'no' to cancel: yes
    

Введемо "yes" і помчали! Чи не прекрасно коли ми можемо змусити комп'ютер друкувати незрозумілий текст сторінка за сторінкою? Кожного разу я додаю невеликий звуковий супровід: Дир-дир-дир...

    Copying '/home/edith/my-first-blog/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/js/actions.min.js'
    Copying '/home/edith/my-first-blog/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/js/inlines.min.js'
    [...]
    Copying '/home/edith/my-first-blog/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/css/changelists.css'
    Copying '/home/edith/my-first-blog/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/css/base.css'
    62 static files copied to '/home/edith/my-first-blog/static'.
    

### Створимо базу даних на PythonAnywhere

Ось ще одна річ, яка відрізняється на локальному комп'ютері та сервері: вони використовують різні бази даних. Так що облікові записи користувачів і статті блогу можуть відрізнятися на сервері і локальному комп'ютері.

Ми можемо ініціалізувати базу даних на сервері таким самим чином, як і на локальному комп'ютері - з допомогою `migrate` і `createsuperuser`:

    (mvenv) $ python manage.py migrate
    Operations to perform:
    [...]
      Applying sessions.0001_initial... OK
    
    
    (mvenv) $ python manage.py createsuperuser
    

## Опублікуємо наш блог як веб-додаток

Тепер наш код на PythonAnywhere, віртуальне середовище готове, статичні файли зібрані, база даних встановлена. Ми готові до публікації веб-додатку!

Перейдемо до панелі керування PythonAnywhere, натиснувши на лого сайту і виберемо вкладку **Web**. Тепер натиснемо **Add a new web app**.

Після підтвердження нашого доменного імені виберемо ручне налаштування (**manual configuration**) у діалоговому вікні, зверніть увагу: варіант "Django" нам *не годиться*. Далі виберемо **Python 3.4** і натиснемо Next для завершення.

> **Примітка** Пересвідчіться, що ви вибрали варіант "Manual configuration", а не "Django". Ми занадто круті для стандартних налаштувань PythonAnywhere для Django ;-)

### Налаштуємо virtualenv

Ми опинились на сторінці налаштувань веб-додатку на PythonAnywhere. Сюди слід іти, якщо ви хочете зробити якісь зміни до додатку на сервері.

![][7]

 [7]: images/pythonanywhere_web_tab_virtualenv.png

У розділі "Vitrualenv" натиснемо на червоний текст "Enter the path to a virtualenv" (введіть шлях до virtualenv) і напишемо: `/home/<your-username>/my-first-blog/myvenv/`. Перед тим як продовжити, натиснемо синю кнопку з галочкою, щоб зберегти шлях.

> **Примітка** Замініть <your-username> на своє ім'я користувача. Якщо ви помилитесь, PythonAnywhere покаже вам невеличке попередження.

### Сконфігуруємо WSGI файл

Django використовує у роботі "WSGI протокол" - стандарт взаємодії веб-додатків на Python із веб-серверами. Він підтримується PythonAnywhere. Отже, поредагувавши конфігураційний файл WSGI, ми дозволимо PythonAnywhere розпізнати наш блог на Django.

Перейдемо за посиланням напроти "WSGI configuration file" (у розділі "Code" близько до початку сторінки -- посилання матиме якусь таку назву: `/var/www/<your-username>_pythonanywhere_com_wsgi.py`). Ми опинились на сторінці з редактором.

Зітремо весь вміст файлу і замінимо його таким:

    python
    import os
    import sys
    
    path = '/home/<your-username>/my-first-blog'  # use your own username here
    if path not in sys.path:
        sys.path.append(path)
    
    os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'
    
    from django.core.wsgi import get_wsgi_application
    from whitenoise.django import DjangoWhiteNoise
    application = DjangoWhiteNoise(get_wsgi_application())
    

> **Примітка** Не забудьте вказати своє ім'я користувача замість `<your-username>`

Завдання цього файлу -- розповісти PythonAnywhere, де живе наш веб-додаток і як знайти файл із налаштуванням Django. Також він налаштовує інструмент для статичних файлів "whitenoise".

Натиснемо **Save** і перейдемо назад до вкладки **Web**.

Готово! Натискаємо на велику зелену **Reload** кнопку і можемо глянути на свій веб-додаток. Посилання на нього вгорі сторінки.

## Підказки для налагодження

Якщо, спробувавши відвідати свій сайт, ви побачили повідомлення про помилку, перше місце, куди слід подивитись - це **лог помилок**. Перейти до нього можна із [вкладки Web][8] PythonAnywhere. Гляньте, чи там є повідомлення про невдачі; найнедавніші будуть внизу файлу. Найчастіше трапляються такі проблеми:

 [8]: https://www.pythonanywhere.com/web_app_setup/

*   Ви забули ввести одну із команд у консолі: створення віртуального середовища, його активацію, встановлення туди Django, збирання статичних файлів, міграцію бази даних.

*   Ви зробили одрук у шляху до virtualenv у вкладці Web -- в такому разі, там можна буде побачити маленьке червоне повідомлення про помилку.

*   Ви помилились у конфігураційному файлі WSGI -- перевірте шлях до своєї директорії my-first-blog.

*   Ви точно вибрали таку ж версію Python для віртуального середовища як і для веб-додатку? Обидві повинні бути 3.4.

*   Ось деякі [загальні підказки для налагодження у PythonAnywhere вікі][9].

 [9]: https://www.pythonanywhere.com/wiki/DebuggingImportError

Пам'ятайте, з вами тренер, щоб допомагати!

# Ми вийшли у світ!

На стандартній сторінці нашого сайту має бути напис "Welcome to Django" так само, як і на вашому локальному комп'ютері. Спробуємо додати `admin` у кінці URL і опинимось на адміністративній панелі сайту. Використаємо для входу логін і пароль і побачимо, що тут можна додавати нові пости на сервер.

*ДОБРЯЧЕ* поплескайте себе по спині! Розгортання на сервер -- один з найхитромудріших етапів веб-розробки. Зазвичай люди витрачають дні, щоб усе запрацювало. Але вам вдалось вийти у справжній інтернет, запросто!