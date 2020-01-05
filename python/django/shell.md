## Django Shell

> 장고 project 설정이 로딩된 shell 

`python` 명령어를 통해 파이썬 shell을 사용할 수 있지만, 프로젝트 구성을 사용할 수 없다. django 에서도  `rails c` 와 같은 기능을 제공하는데, 장고에서는 `python3 manage.py shell` 명령어로 사용한다. 해당 명령어를 통해 `settings.py` 의 내용을 불러와 프로젝트를 구성한다



#### Django shell

```
>>> for post in posts:
...     print(post.title)
... 
zz
```

아쉬운건 import 가 안되서 하나하나 import 를 해줘야 되서 불편한다. 근데! 알고보니 라이브러리가 존재함

## django-extensions

django-extension 을 설정하면 알아서 모듈을 다 불러와준다.

##### 설치

```python
$ pip install django-extensions
```

##### settings.py 적용

installed_app 에 적용해준다.

```python

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
    'django_extensions',
]
```

##### 실행

실행은 `shell_plus` 를 추가해서 붙혀주면 된다

```python
python3 manage.py shell_plus
```

결과

```python
# Shell Plus Model Imports
from blog.models import Post
from django.contrib.admin.models import LogEntry
from django.contrib.auth.models import Group, Permission, User
from django.contrib.contenttypes.models import ContentType
from django.contrib.sessions.models import Session
# Shell Plus Django Imports
from django.core.cache import cache
from django.conf import settings
from django.contrib.auth import get_user_model
from django.db import transaction
from django.db.models import Avg, Case, Count, F, Max, Min, Prefetch, Q, Sum, When, Exists, OuterRef, Subquery
from django.utils import timezone
from django.urls import reverse
Python 3.7.2 (v3.7.2:9a3ffc0492, Dec 24 2018, 02:44:43) 
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> Post.all()
```

