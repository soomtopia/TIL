## [python] error - Non-ASCII character 'xeb' in file file_name.py on line N, but no encoding declared.md

파이썬 파일에 한글 썼을때 나타나는 에러. python 2 이하에서 에러나는듯

#### solve

- python3 으로 실행해준다 

- or

  ```python
  # -*- coding: utf-8 -*-
  ```

  를 붙혀준다.

