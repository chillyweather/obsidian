## Action
| Key | Result      |
| --- | ----------- |
| `v` | select      |
| `y` | copy (yank) |
| `c` | change      |
| `d` | delete      |

## Scope

| Key | Result |
| --- | ------ |
| `a` | around |
| `i` | inside |

## Object

| Key | Result |
| --- | ------ |
| `w` | word |
| `p` | paragraph |
| `s` | sentence |
| `q` | quotes |
| `b` | brackets |
| `o` | block |
| `t` | tag |
| `i` | indention level |
| `W` | white space |

## Examples

| Command | Result |
| --- | ------ |
| `vaq` | select around current word |
| `yiW` | copy between last and next white space |
| `ciq` | change inside quotes |
| `dii` | delete everything at current indention |

## Extra

| Command | Result |
| --- | ------ |
| `f<char>` | find next character, stop on it |
| `t<char>` | find next character, stop before it |
| `F<char>` | find prev character, stop on it |
| `T<char>` | find prev character, stop before it |

| Command | Result                                       |
| ------- | -------------------------------------------- |
| `ct"`   | change from cursor to next " (leaving ")     |
| `df\|`  | delete from cursor to next \| (including \|) |