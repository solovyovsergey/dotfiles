# Настройка рабочего окружения

## Описание

Zsh уже содержит конфиг для nvm и nvm autoload. При установке nvm удалить из файла конфига то, что повторно добавляет установочный скурипт.
// TODO

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

Выкачать репозиторий в удобную папку.
Лучше клонировать, чтобы сохранить возможность подтягивать обновления:

```bash
git clone --depth 1 https://github.com
```

#### Linux

Путь к папке с файлами конфигурации:
`~/.config/alacritty`

#### Windows (для запуска WSL)

> Для запуска wsl из терминала alacritty можно создать ярлык и прописать в поле "Объект" следующее значение:
>
> `alacritty -e wsl -d ubuntu --cd ~`

Путь к папке с файлами конфигурации:
`%APPDATA%\alacritty`

Создаем символическую ссылку на папку конфигурации из нашего репозитория. Ссылку для Windows-приложения (Alacritty) надежнее создавать средствами Windows, т.е через CMD.

```cmd
# удаляем старую папку (если она есть)
rmdir /s /q %APPDATA%\alacritty

# создаем саму ссылку
mklink /D "%APPDATA%\alacritty" "<path\to\your\dotfiles>\alacritty"
# или
mklink /D "C:\Users\<ИМЯ_ПОЛЬЗОВАТЕЛЯ>\AppData\Roaming\alacritty" "<path\to\your\dotfiles>\alacritty"

```

**Для применения конфига перезапустите терминал.**

Если не работает ввод(клик) мышью (например при попытке переместить каретку в самом терминале alacritty или в запущенном текстовом редакторе), то нужно:

- Перейти по ссылке <https://github.com/wezterm/wezterm/tree/main/assets/windows/conhost> и скачать два файла OpenConsole.exe и conpty.dll.
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

## zsh

### Установка

Инструкцию по установке zsh смотри вот здесь:
<https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH>.

Делаем оболочкой по умолчанию:
`chsh -s $(which zsh)`

### Подключаем файл конфигурации .zchrc

Файл конфигурации хранится здесь `~/.zshrc`

```bash
# Удалить старый конфиг (если он есть)
rm -f ~/.zshrc

# Создать символьную ссылку на файл из dotfiles
ln -s ~/path/to/your/dotfiles/zsh/.zshrc ~/.zshrc

```

### Как проверить

```bash
# Должна вернуть версию zsh (например zsh 5.0.8)
zsh --version
# Должна вернуть путь к zsh (например /usr/bin/zs)
echo $SHELL
```

### Установка плагинов

1. Подсветка синтаксиса команд: <https://github.com/zsh-users/zsh-syntax-highlighting>
2. Автодополнение команд: <https://github.com/zsh-users/zsh-autosuggestions>
   Для установки воспользуйтесь вашим пакетным менеджером.

```bash
# для Ubuntu/Debian
sudo apt update && sudo apt install zsh-autosuggestions zsh-syntax-highlighting

# для Arch
sudo pacman -S zsh-autosuggestions zsh-syntax-highlighting
```

### Установка промпта Starship

Процесс установки смотри здесь: <https://starship.rs/>

## VS Code

// TODO
Настроить форматтер shell-format и добавить в раздел с плагинами

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

## TODO

1. Настроить prettier и linter для toml файлов. В частности, чтобы ключ и значение были как в таблице
