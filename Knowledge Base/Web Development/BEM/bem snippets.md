### Как автоматически генерировать структуру в соответствии с BEM
![[Pasted image 20210729194848.png]]

### BEM validator

#### Install

npm i -g bem-validate

#### [](https://github.com/shakyShane/bem-validator#use-on-files)Use on files

Single file:

```
bem-validate index.html
```

Multi files

```
bem-validate index.html about.html
```

Globs

```
bem-validate _site/**/*.html
```

#### [](https://github.com/shakyShane/bem-validator#use-on-urls)Use on URLs

bem-validate http://getbem.com/introduction/