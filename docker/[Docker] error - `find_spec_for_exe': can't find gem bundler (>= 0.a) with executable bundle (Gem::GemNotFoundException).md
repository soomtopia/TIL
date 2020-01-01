## `find_spec_for_exe': can't find gem bundler (>= 0.a) with executable bundle (Gem::GemNotFoundException)

#### error

```
`find_spec_for_exe': can't find gem bundler (>= 0.a) with executable bundle (Gem::GemNotFoundException)
```

도커에 레일즈를 설치하는데 계속 이게 떠서 안됐다. 별걸 다 해봤는데 안되었음..

#### solve

Gemfile.lock 삭제

