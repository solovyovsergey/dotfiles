# Настройка рабочего окружения

## Alacritty

### Установка Alacritty

См. <https://alacritty.org/>.

### Установка шрифтов

Для корректного отображения различных значков и символов, нужно установить шрифты **JetBrainsMono Nerd Font** с ресурса <https://www.nerdfonts.com/font-downloads>

#### Установка шрифтов на Linux

```bash
# 1. Создаем папку (если нет)
mkdir -p ~/.local/share/fonts

# 2. Копируем шрифты
cp *.ttf ~/.local/share/fonts/

# 3. Заставляем систему "увидеть" их
fc-cache -fv
```

#### Установка шрифтов на Windows

- Распаковать загруженный архив со шрифтами.
- Выделить все файлы шрифтов \*.ttf и в меню выбрать "**Установить**" или "**Установить для всех пользователей**"

### Подключаем файл конфигурации

#### Linux

Путь к папке с файлами конфигурации:
`~/.config/alacritty`

#### Windows (для запуска WSL)

Путь к папке с файлами конфигурации:
`%APPDATA%\alacritty`

Если не работает ввод(клик) мышью (например при попытке переместить каретку в самом терминале alacritty или в запущенном текстовом редакторе), то нужно:

- Перейти по ссылке c:\Program Files\Alacritty\ и скачать два файла OpenConsole.exe и conpty.dll.
- Положить эти файлы в папку, куда был установлен alacritty (обычно это c:\Program Files\Alacritty\).

Подробнее проблема и ее решение описаны здесь:

- <https://github.com/alacritty/alacritty/issues/1663>
- <https://github.com/alacritty/alacritty/issues/1663#issuecomment-1917418514>.

### Тестируем

- Проверяем, применилась ли тема.
- Проверяем, применились ли шрифты:

```bash
# проверка начертания шрифтов normal, bold, italic, bold-italic
echo -e "Normal \e[1mBold\e[0m \e[3mItalic\e[0m \e[1;3mBold-Italic\e[0m"
# проверка иконок
echo -e "\uf17c Linux \uf17a Windows \uf484 Alacritty \uf15c File"
```

## VS Code

// TODO

### Тема

<https://marketplace.visualstudio.com/items?itemName=jdinhlife.gruvbox>
С опцией Hard

### Плагины

Для markdown

- Markdown All in One
- markdownlint

Для toml

- Even Better TOML

## tmux

## zsh

## TODO

1. Настроить prettier и linter для toml файлов. В частности, чтобы ключ и значение были как в таблице
