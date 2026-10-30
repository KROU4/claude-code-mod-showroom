# Mod Showroom

**Витрина модов для Claude Code.** Каталог плагинов, которые меняют сам клиент: полосы над полем ввода, панели, строки статуса, уведомления, спиннеры, стражи вызовов инструментов. На сайте каждый мод показан внутри макета клиента, а ставится он одной командой.

**[Открыть сайт](https://krou4.github.io/claude-code-mod-showroom/)** · [English](README.en.md) · [Как добавить мод](CONTRIBUTING.md) · [Исследование](docs/research.md)

[![Sync and deploy](https://github.com/KROU4/claude-code-mod-showroom/actions/workflows/sync.yml/badge.svg?branch=main)](https://github.com/KROU4/claude-code-mod-showroom/actions/workflows/sync.yml)

Сейчас в каталоге <!-- count:start -->266 модов<!-- count:end -->. Репозиторий одновременно служит маркетплейсом Claude Code `mod-showroom`.

## Содержание

- [Что такое мод](#что-такое-мод)
- [Как поставить](#как-поставить)
- [Каталог](#каталог)
- [Добавить свой мод](#добавить-свой-мод)
- [Как защищён репозиторий](#как-защищён-репозиторий)
- [Исследование](#исследование)
- [Связанные проекты](#связанные-проекты)
- [Лицензия](#лицензия)

## Что такое мод

Мод — это плагин Claude Code, у которого `hooks/hooks.json` указывает на модуль с функциями-хуками. Хуки получают события клиента (вызовы инструментов, промпты, отрисовку) и могут дорисовать интерфейс или изменить поведение: показать полосу над промптом, открыть панель, отклонить вызов инструмента. Моды появились в Claude Code 2.1.287 и работают в терминале, в десктопном приложении и частично в панели VS Code.

```text
turn-meter/
├── .claude-plugin/
│   └── plugin.json      имя, версия, описание
└── hooks/
    ├── hooks.json       { "modules": ["./register.tsx"] }
    └── register.tsx     export const register = (on) => { … }
```

## Как поставить

Нужен Claude Code 2.1.287 или новее; в десктопном приложении моды работают со встроенной версии 2.1.286.

**В сессии Claude Code в терминале** достаточно одной команды. Если маркетплейс ещё не добавлен, Claude Code предложит его добавить (нужна версия 2.1.275+):

```text
/plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
```

То же в два шага: один раз добавить маркетплейс, потом ставить моды по имени.

```text
/plugin marketplace add KROU4/claude-code-mod-showroom
/plugin install turn-meter@mod-showroom
```

**Из оболочки** (2.1.292+):

```sh
claude plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
```

Если сессия уже открыта, выполните в ней `/reload-plugins` или начните новую.

**В десктопном приложении** команды `/plugin` нет. Нажмите «+» рядом с полем ввода, выберите Plugins → Add marketplace, введите `KROU4/claude-code-mod-showroom` и затем Add plugin. Мод, поставленный из терминала для пользователя (scope user), загружается и в десктопе.

**В VS Code** мод ставится в один клик по ссылке `vscode://anthropic.claude-code/install-plugin`. GitHub такие ссылки не показывает, поэтому кнопки «Install in VS Code», «Open in terminal» и «Open in Claude desktop» есть на странице каждого мода [на сайте](https://krou4.github.io/claude-code-mod-showroom/).

Мод выполняется внутри вашей сессии с вашими правами. Перед установкой внешнего мода прочитайте его код: ссылка на исходники есть у каждой записи.

## Каталог

Для каждого мода указано, что он рисует, кто автор и где лежит код: «в этом репозитории» — код в `mods/<имя>/plugin/`: его проверяет CI, а изменения после первой версии читает мейнтейнер каталога; «внешний» — код в репозитории автора. Это код сообщества: прочитайте его перед установкой. Под спойлером команда установки.

<!-- mods:start -->
Категории: [Интерфейс](#интерфейс) · [Сводки](#сводки) · [Безопасность](#безопасность) · [Продуктивность](#продуктивность) · [Git](#git) · [Интеграции](#интеграции) · [Для настроения](#для-настроения) · [Доступность](#доступность)

### Интерфейс

- **[bline](https://krou4.github.io/claude-code-mod-showroom/#/mod/bline)** — Модель, уровень рассуждений и заполнение контекста в строке подсказки под полем ввода, всё кликабельно. <sub>рисует: строка подсказки · автор @xchacha20-poly1305 · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install bline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Clarity](https://krou4.github.io/claude-code-mod-showroom/#/mod/clarity)** — Запросы и ответы в рамках, цветные значки инструментов, живая полоса состояния и панель сессии. <sub>рисует: строки инструментов, спиннер, строка длительности хода, панель, строка статуса, всплывающее уведомление, системное уведомление, слеш-команда · автор @CircularBlox · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install clarity --marketplace CircularBlox/Clarity
  ```

  </details>
- **[Claudinator](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudinator)** — Шесть сменных стилей для строк инструментов, индикатора работы и итога хода плюс девять ингредиентов. <sub>рисует: строки инструментов, строка длительности хода, слеш-команда, панель, всплывающее уведомление · автор @patheonsceo · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install claudinator --marketplace patheonsceo/claudinator
  ```

  </details>
- **[Desk Look](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-look)** — Переписка в терминале выглядит как вкладка Code в десктопном приложении, плюс панели диффа, PR и контекста. <sub>рисует: строки инструментов, сообщения в переписке, полоса над полем ввода, панель, слеш-команда · автор @KyongSik-Yoon · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install desk-look --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Drawer](https://krou4.github.io/claude-code-mod-showroom/#/mod/drawer)** — Блоки \`\`\`dot (Graphviz) и \`\`\`svg в ответе превращаются в картинки прямо на месте, пока ответ печатается. <sub>рисует: сообщения в переписке · автор @Sureffi · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install drawer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Figures](https://krou4.github.io/claude-code-mod-showroom/#/mod/figures)** — Диаграммы mermaid, Graphviz, D2 и SVG, формулы LaTeX и картинки инструментов в терминале с kitty-графикой. <sub>рисует: сообщения в переписке, панель, всплывающее уведомление, слеш-команда · автор @natsukium · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install figures --marketplace natsukium/claude-code-figures-plugin
  ```

  </details>
- **[Filetree](https://krou4.github.io/claude-code-mod-showroom/#/mod/filetree)** — Дерево файлов сбоку: статус git, число изменённых строк, а файлы, которые Claude читает и пишет, переливаются. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @data-goblin · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install filetree --marketplace data-goblin/claude-code-filetree
  ```

  </details>
- **[Firelight](https://krou4.github.io/claude-code-mod-showroom/#/mod/firelight)** — Три темы Firelight (Coal, Smoulder, Ash), которые заодно перекрашивают фон терминала под себя. <sub>автор @GarvitNangru · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install firelight --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Firstmate Calm](https://krou4.github.io/claude-code-mod-showroom/#/mod/fm)** — Скрывает строки инструментов и превращает индикатор работы в плывущий парусник; включается командой /calm. <sub>рисует: слеш-команда, всплывающее уведомление, полоса над полем ввода, сообщения в переписке · автор @kunchenguid · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install fm --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Glass](https://krou4.github.io/claude-code-mod-showroom/#/mod/glass)** — Вид десктопного приложения для истории в терминале: цветные команды, карточки кода и диффов, 13 палитр. <sub>рисует: строки инструментов, сообщения в переписке, строка статуса, всплывающее уведомление, системное уведомление, слеш-команда · автор @rashedInt32 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install glass --marketplace rashedInt32/glass
  ```

  </details>
- **[glowup](https://krou4.github.io/claude-code-mod-showroom/#/mod/glowup)** — Панель-кокпит, паки, меняющие цвета, строки инструментов и спиннер, и пиксельный питомец, который реагирует. <sub>рисует: слеш-команда, сообщения в переписке, строки инструментов, спиннер, панель, строка статуса · автор @NovusEdge · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install glowup --marketplace NovusEdge/glowup
  ```

  </details>
- **[Image Peek](https://krou4.github.io/claude-code-mod-showroom/#/mod/image-peek)** — Миниатюры вставленных картинок над полем ввода и картинки покрупнее под каждым отправленным сообщением. <sub>рисует: полоса над полем ввода · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install image-peek --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Image View](https://krou4.github.io/claude-code-mod-showroom/#/mod/image-view)** — Показывает миниатюры вставленных картинок над полем ввода, а не одни теги \[Image \#1\]. <sub>рисует: полоса над полем ввода · автор @jarrodwatts · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install image-view --marketplace jarrodwatts/claude-image-view
  ```

  </details>
- **[Inline Images](https://krou4.github.io/claude-code-mod-showroom/#/mod/inline-images)** — Инструмент show\_image для Claude, а вставленные и прочитанные Claude картинки рисуются прямо в ленте. <sub>рисует: инструмент для Claude · автор @benjaminb10 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install inline-images --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Intelligent UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/intelligent-ui)** — Ответы Claude в виде свёрстанных картинок: таблицы, формулы LaTeX, графики и диаграммы через Typst. <sub>рисует: слеш-команда, сообщения в переписке, всплывающее уведомление, панель · автор @razorback16 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cc-intelligent-ui --marketplace razorback16/cc-intelligent-ui
  ```

  </details>
- **[jr badge](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-badge)** — Цветной значок проекта и его ветка над полем ввода, чтобы не перепутать окна. <sub>рисует: полоса над полем ввода, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-badge --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[mercat](https://krou4.github.io/claude-code-mod-showroom/#/mod/mercat)** — Блоки mermaid в ответах Claude рисуются текстовыми диаграммами, плюс панель для файлов markdown и mermaid. <sub>рисует: сообщения в переписке, панель, всплывающее уведомление, слеш-команда · автор @tawago · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install mercat --marketplace tawago/mercat
  ```

  </details>
- **[Model Effort Band](https://krou4.github.io/claude-code-mod-showroom/#/mod/model-effort-band)** — Цветная полоса над полем ввода: выбранная модель и усилие, с которым прошёл её последний запрос. <sub>рисует: полоса над полем ввода · автор @YeonwooSung · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install model-effort-band --marketplace YeonwooSung/my-claude-code-mods
  ```

  </details>
- **[Paste Peek](https://krou4.github.io/claude-code-mod-showroom/#/mod/paste-peek)** — Windows Terminal: миниатюры вставленных картинок в маленькой полоске, пока вы не отправите запрос. <sub>рисует: всплывающее уведомление · автор @MankhongGarden · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install paste-peek --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Plain View](https://krou4.github.io/claude-code-mod-showroom/#/mod/plain-view)** — Тихий диалог: строки инструментов уходят, а план агента виден карточкой с полосами прогресса. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install plain-view --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Prismantis](https://krou4.github.io/claude-code-mod-showroom/#/mod/prismantis)** — Цветные ответы с темами: таблицы, код, графики и схемы mermaid, тихие строки инструментов, кнопки копирования. <sub>рисует: сообщения в переписке, панель, всплывающее уведомление, слеш-команда · автор @NahumLitvin · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install prismantis --marketplace NahumLitvin/prismantis
  ```

  </details>
- **[Quiet Transcript](https://krou4.github.io/claude-code-mod-showroom/#/mod/quiet-transcript)** — Пояснения по ходу, вызовы инструментов и вывод команд бледнеют; ответы Claude остаются как есть. <sub>рисует: сообщения в переписке, строки инструментов · автор @kevlar10x · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install quiet-transcript --marketplace kevlar10x/quiet-transcript
  ```

  </details>
- **[Readable Layout](https://krou4.github.io/claude-code-mod-showroom/#/mod/readable-layout)** — Ваши сообщения и ответы Claude в подписанных рамках, заметки тихими строками, жирный текст в цвете. <sub>рисует: сообщения в переписке, строка длительности хода · автор @GarvitNangru · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install readable-layout --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Rich UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/rich-ui)** — Диаграммы Mermaid прямо в переписке, просмотр markdown-файлов в панели и не только; каждое можно выключить. <sub>рисует: сообщения в переписке, строка статуса, панель, всплывающее уведомление, слеш-команда · автор @emergentai · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install rich-ui --marketplace emergentai/claude-code-rich-ui
  ```

  </details>
- **[Show Me](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-me)** — Диаграммы mermaid из ответа рисуются картинками в панели, как только ход заканчивается. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install show-me --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Show Paths](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-paths)** — В каждой строке Read, Edit, Write, Glob и Grep в переписке виден путь, с которым работал инструмент. <sub>рисует: строки инструментов, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install show-paths --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Show Your Work](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-your-work)** — Claude показывает скриншоты и записи Playwright прямо в чате: до и после, с проверками QA. <sub>рисует: строки инструментов, инструмент для Claude, слеш-команда, панель, строка статуса, всплывающее уведомление · автор @iamumeransari · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install show-your-work --marketplace iamumeransari/claude-show-your-work
  ```

  </details>
- **[Skins](https://krou4.github.io/claude-code-mod-showroom/#/mod/skins)** — Строки инструментов со статусом, временем и числом правок, карточки вывода и таблиц, полоса лимитов и 15 тем. <sub>рисует: слеш-команда, всплывающее уведомление, строки инструментов, спиннер, строка длительности хода, полоса над полем ввода, инструмент для Claude, панель · автор @hellosverre · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install skins --marketplace hellosverre/claude-skins
  ```

  </details>
- **[Status Line Anywhere](https://krou4.github.io/claude-code-mod-showroom/#/mod/statusline-anywhere)** — Запускает вашу команду statusLine и рисует её вывод в цвете над полем ввода в десктопном приложении. <sub>рисует: полоса над полем ввода · автор @NathanAB · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install statusline-anywhere --marketplace NathanAB/statusline-anywhere
  ```

  </details>
- **[Stretchtext Replies](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-stretch)** — Ответы приходят короткими: нажмите на подчёркнутую фразу, и она развернётся на месте в подробный текст. <sub>рисует: сообщения в переписке, слеш-команда, полоса над полем ввода, всплывающее уведомление · автор @pro-vi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cc-stretch --marketplace pro-vi/cc-stretch
  ```

  </details>
- **[TL;DR](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-tldr)** — Каждый ход свёрнут в одну строку: какие файлы изменены, тесты до и после и что стоит проверить. <sub>рисует: сообщения в переписке, системное уведомление, панель, строка статуса, слеш-команда · автор @kushalBanda · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install tldr --marketplace kushalBanda/claude-tldr
  ```

  </details>
- **[Veneer](https://krou4.github.io/claude-code-mod-showroom/#/mod/veneer)** — Подсветка синтаксиса для 100+ языков в любой теме VS Code, диаграммы, формулы и картинки в чате. <sub>рисует: строки инструментов, сообщения в переписке, панель, слеш-команда · автор @MitchMedeiros · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install veneer --marketplace MitchMedeiros/veneer
  ```

  </details>

### Сводки

- **[Agent Monitor](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-monitor)** — Полоса прогресса над полем ввода, которая заполняется по ходу плана Claude, и панель субагентов. <sub>рисует: полоса над полем ввода, панель, слеш-команда, инструмент для Claude · автор @GarvitNangru · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install agent-monitor --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Agent Radar](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-radar)** — Живая строка над полем ввода на каждый работающий субагент и фоновую команду: время, инструменты, текущий шаг. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда, панель · автор @hamzafer · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install agent-radar --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Agent Tree](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-tree)** — Боковая панель рисует агентов сессии деревом блоков; остановить агента или сменить модель можно кликом. <sub>рисует: панель, строка статуса, всплывающее уведомление, слеш-команда · автор @MikeGT4 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install agent-tree --marketplace MikeGT4/agent-tree
  ```

  </details>
- **[Agent Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-watch)** — Субагенты с первого взгляда: карточка с талисманом, шагом и токенами и уведомление о зависании. <sub>рисует: строка статуса, всплывающее уведомление, панель, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install agent-watch --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Ant Farm](https://krou4.github.io/claude-code-mod-showroom/#/mod/ant-farm)** — Пульт сабагентов: живая карточка на каждого со статусом, токенами, оценкой стоимости и временем до конца. <sub>рисует: полоса над полем ввода, панель, строка статуса, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ant-farm --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Burn Baby Burn](https://krou4.github.io/claude-code-mod-showroom/#/mod/burn-baby-burn)** — Шкалы использования за сессию и неделю под полем ввода и огненные напоминания, если неделя пропадает зря. <sub>рисует: строка подсказки, всплывающее уведомление, слеш-команда, строка статуса · автор @qorvyx · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install burn-baby-burn --marketplace qorvyx/burn-baby-burn
  ```

  </details>
- **[Burn Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/burn-meter)** — Стоимость сессии над полем ввода: огненная полоса, лимиты тарифа и цена в буррито. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда, панель · автор @OneWave-AI · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install burn-meter --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Cache Clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-clock)** — Строка кэша промпта под строкой статуса: сколько кэш ещё тёплый, доля попаданий, промахи, токены на перекэш. <sub>рисует: слеш-команда, строка статуса · автор @hamzafer · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cache-clock --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Cache Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-meter)** — Доля попаданий в кэш промпта и время до его остывания над полем ввода, с переключателем Keep warm. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @T-AI-Labs · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cache-meter --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[Cache Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-timer)** — Обратный отсчёт над полем ввода до истечения кэша промпта и сколько токенов перезапишет холодный кэш. <sub>рисует: полоса над полем ввода · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install cache-timer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Claude Carbon](https://krou4.github.io/claude-code-mod-showroom/#/mod/carbon-footprint)** — Оценка выбросов CO2 каждого ответа и всей сессии и панель с пиксельной молекулой в десктопном приложении. <sub>рисует: строка длительности хода, полоса над полем ввода, панель, строка статуса, всплывающее уведомление, слеш-команда · автор @gwittebolle · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install claude-carbon --marketplace gwittebolle/claude-carbon
  ```

  </details>
- **[Claude Context Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-status-bar)** — Полоса над полем ввода со сменными скинами: контекст, пятичасовой лимит, git, время хода и возраст сессии. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @eddywong888 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install context-bar --marketplace eddywong888/claude-context-bar
  ```

  </details>
- **[Cockpit](https://krou4.github.io/claude-code-mod-showroom/#/mod/cockpit)** — Одна живая панель: агенты, кэш, контекст, токены, лимиты, файлы, проверки разрешений и журнал. <sub>рисует: панель, полоса над полем ввода, слеш-команда · автор @bharath-gp · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cockpit --marketplace bharath-gp/ai-harness
  ```

  </details>
- **[Code Display](https://krou4.github.io/claude-code-mod-showroom/#/mod/st-code-display)** — Панель в стиле OLED для чтения: модель и лимиты, агенты, советы архитектора, инструменты, файлы и журнал. <sub>рисует: панель, слеш-команда · автор @sergios-tech · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install st-code-display --marketplace sergios-tech/code-display
  ```

  </details>
- **[Command Clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/cccc)** — Сколько уже идёт каждая команда Bash на переднем плане — тусклой строкой под её вызовом. <sub>рисует: строки инструментов · автор @xchacha20-poly1305 · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install cccc --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Context Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-bar)** — Составная полоса над полем ввода: чем занято окно контекста и когда начнётся автосжатие. <sub>рисует: полоса над полем ввода, слеш-команда · автор @hamzafer · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install context-bar --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Context Gauge](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-gauge)** — Заполненность окна контекста прямо в строке подсказки под полем ввода. <sub>рисует: строка подсказки · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install context-gauge --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Context Usage](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-usage)** — Заполнение контекста с порогом автосжатия, кнопки Compact и Clear и лимиты на 5 часов и неделю. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @T-AI-Labs · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install context-usage --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[Cost Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/cost-meter)** — Стоимость сессии, контекст и лимиты в строке статуса, цена каждого хода и необязательный бюджет. <sub>рисует: строка длительности хода, строка статуса, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cost-meter --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Files Touched](https://krou4.github.io/claude-code-mod-showroom/#/mod/files-touched)** — Все файлы, которые Claude изменил за сессию, в полосе над полем ввода, со счётчиками +/− и @-ссылками. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install files-touched --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Fine Print](https://krou4.github.io/claude-code-mod-showroom/#/mod/fine-print)** — Небольшая модель перечитывает длинные ответы и отмечает скрытые расходы, риски и необратимые шаги. <sub>рисует: полоса над полем ввода, панель, строка статуса, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install fine-print --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Flightdeck](https://krou4.github.io/claude-code-mod-showroom/#/mod/flightdeck)** — Живая панель сессии: контекст и стоимость, все проверки разрешений, субагенты и журнал событий. <sub>рисует: слеш-команда, панель, строка статуса · автор @scasella · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install flightdeck --marketplace scasella/claude-flightdeck
  ```

  </details>
- **[Footprints](https://krou4.github.io/claude-code-mod-showroom/#/mod/footprints)** — Живое дерево файлов на панели: видно, что Claude прочитал, изменил, создал, удалил и закоммитил. <sub>рисует: панель, строка статуса, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install footprints --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Headway](https://krou4.github.io/claude-code-mod-showroom/#/mod/headway)** — Строка над полем ввода: этап плана, текущий шаг, сколько шагов сделано и сколько примерно осталось. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда, инструмент для Claude · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install headway --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[jr cache clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-cache-clock)** — Уведомление за 30 секунд до остывания кэша промптов и обратный отсчёт над полем ввода по желанию. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-cache-clock --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr context](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-context)** — Окно контекста одной тихой строкой над полем ввода, которая становится тревогой перед сжатием. <sub>рисует: полоса над полем ввода, панель, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-context --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr heatmap](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-heatmap)** — Последние 26 недель с Claude Code в виде тепловой карты как на GitHub, с сериями и пиковыми часами. <sub>рисует: панель, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-heatmap --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-limits)** — Лимиты плана на 5 часов и 7 дней одной тихой строкой над полем ввода, с уведомлениями на 80% и 95%. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-limits --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Limit Lens](https://krou4.github.io/claude-code-mod-showroom/#/mod/limit-lens)** — Доля этой сессии в ваших 5-часовом и недельном лимитах и сколько та же работа стоила бы на каждой модели. <sub>рисует: полоса над полем ввода, панель, слеш-команда · автор @cristi71000 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install limit-lens --marketplace cristi71000/limit-lens
  ```

  </details>
- **[Limits Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/limits-meter)** — Модель, лимиты тарифа, обратный отсчёт кэша промпта и контекст по группам в одной полосе над вводом. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install limits-meter --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Memory Lint](https://krou4.github.io/claude-code-mod-showroom/#/mod/memory-lint)** — Проверяет, укладывается ли индекс автопамяти MEMORY.md в лимит строк, и называет записи за его пределами. <sub>рисует: строка статуса, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install memory-lint --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Owner Rep](https://krou4.github.io/claude-code-mod-showroom/#/mod/owner-rep)** — Следит за агентом и простыми словами говорит, что готово, что упущено и что ему написать дальше. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @macollins27 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install owner-rep --marketplace macollins27/owner-rep
  ```

  </details>
- **[Play-by-Play](https://krou4.github.io/claude-code-mod-showroom/#/mod/play-by-play)** — Пошагово показывает все изменения файлов за ход, включая сделанные командами в shell. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install play-by-play --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Rabe](https://krou4.github.io/claude-code-mod-showroom/#/mod/rabe)** — Вся фоновая работа Claude Code: субагенты, задачи Codex, оболочки, мониторы, cron-задачи и workflow. <sub>рисует: полоса над полем ввода, панель, слеш-команда · автор @lorenzh · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install rabe --marketplace lorenzh/rabe
  ```

  </details>
- **[Redline](https://krou4.github.io/claude-code-mod-showroom/#/mod/redline)** — Заполнение контекста, окна тарифа, стоимость и темп в строке статуса; уведомление при 80% контекста. <sub>рисует: строка статуса, всплывающее уведомление, слеш-команда, панель · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install redline --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Search Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/search-meter)** — Считает поиски Claude под полем ввода: нашёл с первого раза, после промахов или ничего не нашёл. <sub>рисует: строка статуса · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install search-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Band](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-band)** — Ход, обратный отсчёт кеша, скорость, контекст и лимиты 5 ч/неделя над полем ввода, плюс панель активности. <sub>рисует: полоса над полем ввода, панель, системное уведомление, всплывающее уведомление, слеш-команда · автор @KhoaaTran · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install session-band --marketplace KhoaaTran/session-band
  ```

  </details>
- **[Session Info](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-info)** — Одна панель, 13 карточек: контекст и кэш, последний ход, задачи, CI, Jira, лимиты, агенты, проверки, git. <sub>рисует: панель, слеш-команда · автор @dougcunha · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install session-info --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-meter)** — Панель /ctx: контекст по категориям, лимиты и темп их расхода, вызовы инструментов и запросы к модели. <sub>рисует: панель, всплывающее уведомление, слеш-команда, инструмент для Claude · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install session-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Models](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-models)** — Основная модель и усилие, все работающие агенты по моделям и усилию и предупреждения о толпе агентов. <sub>рисует: полоса над полем ввода, всплывающее уведомление, строка статуса · автор @AbhiramDwivedi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install session-models --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Sub Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/sub-meter)** — Расход подписки за 5 часов и за неделю полосой со временем до сброса, в правом нижнем углу. <sub>рисует: строка подсказки, метка режима · автор @midudev · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install sub-meter --marketplace midudev/better-claude
  ```

  </details>
- **[Subagents Plus](https://krou4.github.io/claude-code-mod-showroom/#/mod/subagents-plus)** — Живое дерево и шкала времени всех субагентов в панели /subagents, плюс полоса над полем ввода. <sub>рисует: полоса над полем ввода, слеш-команда, панель, инструмент для Claude · автор @algonormative · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install subagents-plus --marketplace algonormative/subagents-plus
  ```

  </details>
- **[Test Pulse](https://krou4.github.io/claude-code-mod-showroom/#/mod/test-pulse)** — Каждый прогон тестов Claude попадает в строку статуса; уведомление, когда тесты краснеют или зеленеют. <sub>рисует: строка статуса, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install test-pulse --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Time Blame](https://krou4.github.io/claude-code-mod-showroom/#/mod/time-blame)** — Под каждым ответом время хода по частям: Claude, инструменты, вы и прочее; /blame подводит итог сессии. <sub>рисует: строка длительности хода, слеш-команда, панель · автор @karanb192 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install time-blame --marketplace karanb192/time-blame
  ```

  </details>
- **[Token Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-meter)** — Токены каждого хода (вход, вывод, кэш) и итог сессии — цветом в строке под полем ввода. <sub>рисует: строка подсказки · автор @midudev · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install token-meter --marketplace midudev/better-claude
  ```

  </details>
- **[Token Optimizer](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-optimizer)** — Проверяет и урезает то, чем забит контекст; в десктопном приложении — полоса здоровья сессии с Clawd. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @alexgreensh · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install token-optimizer --marketplace alexgreensh/token-optimizer
  ```

  </details>
- **[Token Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-watch)** — Расход тарифа с темпом, контекст по категориям и отсчёт кэша промпта в баннере над полем ввода. <sub>рисует: полоса над полем ввода, системное уведомление, слеш-команда · автор @nevermemo · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install token-watch --marketplace nevermemo/token-watch
  ```

  </details>
- **[Token Weather](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-weather)** — Заполненность контекста как погода над полем ввода: значок, процент, токены и график последних 12 ходов. <sub>рисует: полоса над полем ввода · автор @anthropics · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install token-weather --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Tool Radar](https://krou4.github.io/claude-code-mod-showroom/#/mod/tool-radar)** — Панель со всеми вызовами инструментов: статус, аргументы, длительность и причина ошибки, включая субагентов. <sub>рисует: панель, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install tool-radar --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Tool Timeline](https://krou4.github.io/claude-code-mod-showroom/#/mod/tool-timeline)** — Панель со всеми вызовами инструментов по ходу работы: статус, файл или команда и время вызова. <sub>рисует: слеш-команда, панель · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install tool-timeline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Footer](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-footer)** — Итог под каждым ответом (инструменты, запросы, токены, попадание в кэш) и текущий инструмент в спиннере. <sub>рисует: спиннер, сообщения в переписке · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install turn-footer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-meter)** — Время, вызовы инструментов и токены каждого хода над полем ввода, с мини-графиком последних 12 ходов. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Stats](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-stats)** — Под строкой окончания хода: вызовы по инструментам, ошибки, изменённые файлы и стоимость. <sub>рисует: строка длительности хода, сообщения в переписке · автор @StanislavKozachenko · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install turn-stats --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Turn Timeline](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-timeline)** — Панель /timeline: текущий ход дорожками запросов к модели и вызовов инструментов, с самыми медленными шагами. <sub>рисует: панель, слеш-команда · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install turn-timeline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-timer)** — Тикающий таймер над полем ввода, пока Claude работает, а затем время, за которое пришёл ответ. <sub>рисует: полоса над полем ввода · автор @thecodefeels · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install turn-timer --marketplace thecodefeels/claude-code-turn-timer
  ```

  </details>
- **[Usage Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-bar)** — Контекст, стоимость и лимиты подписки тихой строкой над полем ввода, с предупреждением об остывшем кэше. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @andrej-kolic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install usage-bar --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Usage Limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-limits)** — Лимиты на 5 часов и неделю со скоростью расхода и прогнозом, плюс контекст, стоимость и сбросы кэша. <sub>рисует: полоса над полем ввода, всплывающее уведомление, строка статуса · автор @AbhiramDwivedi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install usage-limits --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Usage Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-meter)** — Киберпанк-полоса с лимитами плана, контекстом и токенами и панель с графиками, агентами, git и PR. <sub>рисует: полоса над полем ввода, панель, слеш-команда · автор @PointerLex · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install usage-meter --marketplace PointerLex/claude-usage-meter
  ```

  </details>
- **[Usage Stats](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-stats)** — /usage-stats открывает тепловую карту токенов, историю по моделям, график по часам и карточку в стиле Wrapped. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @connorchuang32 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install usage-stats --marketplace connorchuang32/claude-usage-stats
  ```

  </details>
- **[WeekToken](https://krou4.github.io/claude-code-mod-showroom/#/mod/weektoken)** — Темп расхода лимитов: сколько потрачено за 5 часов и за неделю против прошедшего времени, прогноз и история. <sub>рисует: полоса над полем ввода, панель, слеш-команда, всплывающее уведомление · автор @3dnow · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install weektoken --marketplace 3dnow/claude-mods
  ```

  </details>
- **[What's Agent Doing](https://krou4.github.io/claude-code-mod-showroom/#/mod/whats-agent-doing)** — Рамка над полем ввода: что агент делает прямо сейчас и как долго, а по нажатию ▸ — пройденные шаги. <sub>рисует: полоса над полем ввода · автор @tzafrir · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install whats-agent-doing --marketplace tzafrir/whats-agent-doing
  ```

  </details>

### Безопасность

- **[Agent Usage Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-usage-guard)** — Сдерживает лавину субагентов, тяжёлые по контексту запросы и циклы повторов, пока они не съели лимит. <sub>рисует: блокировка инструментов, строка статуса, слеш-команда · автор @rbartoli · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install agent-usage-guard --marketplace rbartoli/agent-usage-guard
  ```

  </details>
- **[Bash Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/bash-guard)** — Блокирует катастрофические команды оболочки и спрашивает перед рискованными, даже в режиме без разрешений. <sub>рисует: блокировка инструментов, всплывающее уведомление, сообщения в переписке, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install bash-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Blast Radius](https://krou4.github.io/claude-code-mod-showroom/#/mod/blast-radius)** — Задерживает опасную команду и показывает, какие файлы, коммиты или миграции она затронет: Proceed или Cancel. <sub>рисует: панель, блокировка инструментов, всплывающее уведомление · автор @anthropics · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install blast-radius --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Bouncer](https://krou4.github.io/claude-code-mod-showroom/#/mod/bouncer)** — Показывает, до чего может дотянуться каждый установленный мод, по отчёту валидатора плагинов Claude Code. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install bouncer --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[ccpii](https://krou4.github.io/claude-code-mod-showroom/#/mod/ccpii)** — Имена, почта, телефоны и другие личные данные доходят до модели как пронумерованные заглушки. <sub>рисует: переписывание промпта, строка статуса, всплывающее уведомление, слеш-команда · автор @xchacha20-poly1305 · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install ccpii --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Circuit Breaker](https://krou4.github.io/claude-code-mod-showroom/#/mod/circuit-breaker)** — Если одна и та же команда упала N раз подряд, следующая попытка ждёт вашего решения: остановить или ещё раз. <sub>рисует: блокировка инструментов, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install circuit-breaker --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Cloakroom](https://krou4.github.io/claude-code-mod-showroom/#/mod/cloakroom)** — Секреты доходят до Claude жетонами; настоящее значение вернётся только в локальных правках и командах. <sub>рисует: блокировка инструментов, полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cloakroom --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Command Explainer](https://krou4.github.io/claude-code-mod-showroom/#/mod/command-explainer)** — Простое объяснение того, что сделает команда оболочки, с оценкой риска, прямо там, где вы её одобряете. <sub>рисует: строки инструментов, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install command-explainer --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Fence](https://krou4.github.io/claude-code-mod-showroom/#/mod/fence)** — Одна команда /fence ограничивает, какие пути Claude может править в проекте; правки за пределами отклоняются. <sub>рисует: слеш-команда, блокировка инструментов · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install fence --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[File Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/file-guard)** — Держит правки Claude внутри проекта; lock-файлы, CI, миграции и секреты требуют подтверждения. <sub>рисует: блокировка инструментов, сообщения в переписке, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install file-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/guard)** — Не пускает разрушительные команды и чтение секретных файлов в любой части команды, в Bash и PowerShell. <sub>рисует: блокировка инструментов, строка статуса, всплывающее уведомление, слеш-команда · автор @StanislavKozachenko · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install guard --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Guardrails](https://krou4.github.io/claude-code-mod-showroom/#/mod/ai-harness-guardrails)** — Десять модов для безопасности и проверки: удержание опасных команд, блок секретов, критика, коуч запросов. <sub>рисует: блокировка инструментов, полоса над полем ввода, слеш-команда · автор @bharath-gp · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install guardrails --marketplace bharath-gp/ai-harness
  ```

  </details>
- **[Guardrails](https://krou4.github.io/claude-code-mod-showroom/#/mod/guardrails)** — Отклоняет shell-команды, которые вы включите в /config: деплой cf, строки атрибуции, ветки claude/. <sub>рисует: блокировка инструментов · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install guardrails --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Injection Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/injection-guard)** — Убирает скрытые символы из результатов инструментов и помечает текст, который пытается командовать Claude. <sub>рисует: всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install injection-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[jr deploy guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-deploy-guard)** — Деплой в прод и пуш в main всегда ждут вашего «да», что бы ни разрешали правила. <sub>рисует: блокировка инструментов · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-deploy-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr done-check](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-done-check)** — Отмечает ответы со словами «проверено» или «всё работает», если за ход ничего не запускалось. <sub>рисует: сообщения в переписке, всплывающее уведомление · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-done-check --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr explain](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-explain)** — Каждая команда, которую Claude просит запустить, получает объяснение простыми словами и уровень риска. <sub>рисует: всплывающее уведомление · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-explain --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr image guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-image-guard)** — Не пускает в разговор слишком большие картинки: Claude читает уменьшенную копию. <sub>рисует: строки инструментов, всплывающее уведомление · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-image-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr mod audit](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-mod-audit)** — Посмотрите на мод до установки: до чего он дотягивается, с зелёной, жёлтой или красной оценкой. <sub>рисует: слеш-команда, панель · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-mod-audit --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Last Look](https://krou4.github.io/claude-code-mod-showroom/#/mod/last-look)** — Задерживает разрушительные команды до вашего решения и показывает, какие файлы, правки и коммиты под угрозой. <sub>рисует: панель, строка статуса, блокировка инструментов · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install last-look --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Loadout](https://krou4.github.io/claude-code-mod-showroom/#/mod/loadout)** — Менеджер модов: неодобренные моды и версии не загружаются, пока Claude их не проверит и вы не одобрите. <sub>рисует: всплывающее уведомление, полоса над полем ввода, панель, слеш-команда · автор @Br4inergy · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install loadout --marketplace Br4inergy/claude-loadout
  ```

  </details>
- **[Loop Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/loop-guard)** — Если один и тот же вызов дважды падает с той же ошибкой, Claude получает указание сменить подход. <sub>рисует: всплывающее уведомление · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install loop-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Mulligan](https://krou4.github.io/claude-code-mod-showroom/#/mod/mulligan)** — Сохраняет файлы перед разрушительной командой в shell; /mulligan restore возвращает их обратно. <sub>рисует: полоса над полем ввода, слеш-команда, панель, всплывающее уведомление · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install mulligan --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Net Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/net-guard)** — Сверяет каждый curl, wget, ssh, scp, git push и WebFetch со списками разрешённых и запрещённых хостов. <sub>рисует: блокировка инструментов, сообщения в переписке, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install net-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Package Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/pkg-guard)** — Задерживает установку несуществующих, совсем новых или почти не скачиваемых пакетов, с фактами из реестра. <sub>рисует: блокировка инструментов, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pkg-guard --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Receipts](https://krou4.github.io/claude-code-mod-showroom/#/mod/receipts)** — Claude пишет, что тесты проходят, а Receipts проверяет, был ли после правки реальный прогон. <sub>рисует: сообщения в переписке, полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @candygoogy · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install receipts --marketplace candygoogy/notary
  ```

  </details>
- **[Redact](https://krou4.github.io/claude-code-mod-showroom/#/mod/redact)** — Ключи, токены и пароли из вывода инструментов заменяются до того, как их прочтёт модель. <sub>рисует: строка статуса, всплывающее уведомление, слеш-команда · автор @StanislavKozachenko · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install redact --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Sandbox Tuner](https://krou4.github.io/claude-code-mod-showroom/#/mod/sandbox-tuner)** — Объясняет каждую блокировку песочницы, а повторяющиеся превращает в проверяемые правки настроек с отменой. <sub>рисует: полоса над полем ввода, слеш-команда · автор @dot-agi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install sandbox-tuner --marketplace dot-agi/sandbox-tuner
  ```

  </details>
- **[Scope Cop](https://krou4.github.io/claude-code-mod-showroom/#/mod/scope-cop)** — Задайте, какие файлы можно менять в задаче; правки за этой границей отмечаются или блокируются. <sub>рисует: слеш-команда, полоса над полем ввода, блокировка инструментов, панель, всплывающее уведомление · автор @candygoogy · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install scope-cop --marketplace candygoogy/notary
  ```

  </details>
- **[Secret Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/secret-guard)** — Не даёт Claude читать .env, приватные ключи и файлы с учётными данными. <sub>рисует: блокировка инструментов, всплывающее уведомление, строка статуса · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install secret-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Secret Shield](https://krou4.github.io/claude-code-mod-showroom/#/mod/secret-shield)** — Ключи, токены и пароли в выводе инструментов становятся \[REDACTED:вид\] до того, как их увидит Claude. <sub>рисует: всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install secret-shield --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Style Cop](https://krou4.github.io/claude-code-mod-showroom/#/mod/style-cop)** — Следит за стилем в каждой правке: запрещённые слова, предел доли комментариев и файлы без комментариев. <sub>рисует: блокировка инструментов, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install style-cop --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Subagent Limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/subagent-limits)** — Держит субагентов небольшими: правила дробления, просьба сохраниться и отказ в инструментах за лимитом. <sub>рисует: блокировка инструментов, всплывающее уведомление · автор @AbhiramDwivedi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install subagent-limits --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>

### Продуктивность

- **[Aim](https://krou4.github.io/claude-code-mod-showroom/#/mod/aim)** — Одна цель на сессию над полем ввода с таймером; Claude просят держаться её. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install aim --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Allowlist Coach](https://krou4.github.io/claude-code-mod-showroom/#/mod/allowlist-coach)** — Считает одобренные запросы разрешений и предлагает разрешить правило, когда оно повторяется. <sub>рисует: всплывающее уведомление, панель, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install allowlist-coach --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[aside](https://krou4.github.io/claude-code-mod-showroom/#/mod/aside)** — Копите запросы, идеи и комментарии, пока Claude работает, и отправляйте их, когда он закончит. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда, инструмент для Claude · автор @gravityXX · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install aside --marketplace gravityXX/aside
  ```

  </details>
- **[Bang Commands](https://krou4.github.io/claude-code-mod-showroom/#/mod/bang-commands)** — Когда Claude просит выполнить \`\! команду\` самому, щёлкните по ней, и она окажется в поле ввода. <sub>рисует: сообщения в переписке, полоса над полем ввода, строка статуса, всплывающее уведомление · автор @benjaminb10 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install bang-commands --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Beacon](https://krou4.github.io/claude-code-mod-showroom/#/mod/beacon)** — Значок статуса в начале названия каждой сессии в десктопе: работает, ждёт, нужны вы, готово, ошибка. <sub>автор @VaitaR · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install beacon --marketplace VaitaR/claude-code-beacon
  ```

  </details>
- **[Beads UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/beads-ui)** — Задачи Beads в Claude Code: счётчики сессии над полем ввода и панель с доской, бэклогом и хронологией. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, системное уведомление, слеш-команда · автор @sergeiwallace · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install beads-ui --marketplace sergeiwallace/beads-ui
  ```

  </details>
- **[Big Output](https://krou4.github.io/claude-code-mod-showroom/#/mod/big-output)** — Огромный вывод команд не забивает контекст: Claude видит начало и конец, а остальное листает по запросу. <sub>рисует: инструмент для Claude, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install big-output --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Bookmarks](https://krou4.github.io/claude-code-mod-showroom/#/mod/bookmarks)** — Метки в стиле Vim, позиция чтения и нумерованный список запросов для навигации по длинному диалогу. <sub>рисует: полоса над полем ввода, панель, сообщения в переписке, слеш-команда · автор @DazzleML · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install bookmarks --marketplace DazzleML/claude-bookmarks
  ```

  </details>
- **[Catalog Pane](https://krou4.github.io/claude-code-mod-showroom/#/mod/catalog-pane)** — /catalog показывает все навыки, команды, агенты, моды, плагины, хуки, MCP-серверы и инструменты. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @T-AI-Labs · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install catalog-pane --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[cc-esol](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-esol)** — Тренер английского: ваши запросы на английском исправляются в локальный журнал, который можно разбирать. <sub>рисует: инструмент для Claude, панель, строка подсказки, всплывающее уведомление, слеш-команда · автор @rapha-rodrigues · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cc-esol --marketplace rapha-rodrigues/cc-esol
  ```

  </details>
- **[Claudeopticon](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudeopticon)** — Файлы задач как живая доска тикетов рядом с чатом, связанная с тем, что делают Claude и его агенты. <sub>рисует: панель, слеш-команда · автор @Marceux-Croix · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install claudeopticon --marketplace Marceux-Croix/Claudeopticon
  ```

  </details>
- **[Clear Resume](https://krou4.github.io/claude-code-mod-showroom/#/mod/clear-resume)** — Перед /clear Claude пишет записку-передачу, и новая сессия начинается с неё. <sub>рисует: строка статуса, слеш-команда, всплывающее уведомление · автор @m4cd4r4 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install clear-resume --marketplace m4cd4r4/clear-resume
  ```

  </details>
- **[Command Buttons](https://krou4.github.io/claude-code-mod-showroom/#/mod/command-buttons)** — Кнопки Run и Copy для каждой команды оболочки в ответе и полоса горячих клавиш над полем ввода. <sub>рисует: сообщения в переписке, полоса над полем ввода, всплывающее уведомление · автор @Faridmurzone · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install command-buttons --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Compact Keeper](https://krou4.github.io/claude-code-mod-showroom/#/mod/compact-keeper)** — Сохраняет сводку каждого сжатия контекста и файлы, правленные до него, в \~/.claude/handoffs. <sub>рисует: всплывающее уведомление · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install compact-keeper --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Copy Last](https://krou4.github.io/claude-code-mod-showroom/#/mod/copy-last)** — Копирует последний ответ Claude или его последний блок кода в буфер обмена чистым Markdown по /copy-last. <sub>рисует: слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install copy-last --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[copy-back](https://krou4.github.io/claude-code-mod-showroom/#/mod/copy-back)** — Скопируйте кусок ответа из терминала, наберите /cc, и в буфере окажется исходный текст Claude. <sub>рисует: слеш-команда, всплывающее уведомление · автор @sairam0424 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install copy-back --marketplace sairam0424/claude-copy-back
  ```

  </details>
- **[Crossroads](https://krou4.github.io/claude-code-mod-showroom/#/mod/crossroads)** — После каждого хода над полем ввода три кликабельных следующих запроса, рискованные помечены (deploys, pushes). <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install crossroads --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[ctx-handoff](https://krou4.github.io/claude-code-mod-showroom/#/mod/ctx-handoff)** — Передаёт длинную сессию в новый чат, держит кэш тёплым, пока вас нет, и ведёт заметки проекта. <sub>рисует: полоса над полем ввода, строка статуса, слеш-команда, блокировка инструментов, всплывающее уведомление · автор @cablate · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ctx-handoff --marketplace cablate/ctx-handoff-mod
  ```

  </details>
- **[Daily Standup](https://krou4.github.io/claude-code-mod-showroom/#/mod/daily-standup)** — Записывает каждый ход во всех сессиях; /standup превращает сегодняшнюю работу в короткую сводку. <sub>рисует: слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install standup --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Ding](https://krou4.github.io/claude-code-mod-showroom/#/mod/ding)** — Два разных звука и системное уведомление: один, когда Claude закончил, другой, когда ему нужны вы. <sub>рисует: системное уведомление, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ding --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Done Ding](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-ding)** — Уведомление на рабочем столе и звук, когда долгий ход закончен или Claude ждёт вас; пуш на телефон по желанию. <sub>рисует: системное уведомление, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install done-ding --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Done Notify](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-notify)** — Системное уведомление по окончании долгого хода: Claude закончил или ждёт вашего ответа. <sub>рисует: системное уведомление · автор @benjaminb10 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install done-notify --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Done Ping](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-ping)** — Системное уведомление, когда долгий ход закончился: можно не следить за экраном. <sub>рисует: системное уведомление, слеш-команда, всплывающее уведомление · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install done-ping --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Downrange](https://krou4.github.io/claude-code-mod-showroom/#/mod/downrange)** — Прогресс, оставшееся время и последняя строка вывода фоновых команд и Monitor — по их настоящему выводу. <sub>рисует: полоса над полем ввода, слеш-команда, панель · автор @dot-agi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install downrange --marketplace dot-agi/downrange
  ```

  </details>
- **[effortless](https://krou4.github.io/claude-code-mod-showroom/#/mod/effortless)** — Сам выбирает уровень рассуждений для каждого запроса и показывает над полем ввода, сколько ещё живёт кэш. <sub>рисует: полоса над полем ввода, строка длительности хода, слеш-команда · автор @HeyCubit · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install effortless --marketplace HeyCubit/effortless
  ```

  </details>
- **[Feature Progress](https://krou4.github.io/claude-code-mod-showroom/#/mod/feature-progress)** — Инструмент отчёта для любого процесса по спецификации: полоса прогресса над полем ввода и панель задач. <sub>рисует: инструмент для Claude, полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @dougcunha · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install feature-progress --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Focus Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/focus-timer)** — Помодоро-таймер над полем ввода: пауза, стоп и уведомление в конце сессии. <sub>рисует: слеш-команда, полоса над полем ввода, всплывающее уведомление, системное уведомление · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install focus-timer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Foundry](https://krou4.github.io/claude-code-mod-showroom/#/mod/foundry)** — Выполняет большую задачу параллельными командами агентов в worktree; каждую проверяет судья перед слиянием. <sub>рисует: блокировка инструментов, всплывающее уведомление, слеш-команда · автор @AbhiramDwivedi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install foundry --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Goal Pin](https://krou4.github.io/claude-code-mod-showroom/#/mod/goal-pin)** — Цель разговора закреплена над полем ввода вместе со временем, которое вы над ней работаете. <sub>рисует: слеш-команда, полоса над полем ввода · автор @timoncool · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install goal-pin --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[High Command](https://krou4.github.io/claude-code-mod-showroom/#/mod/high-command)** — Один почтовый ящик для сообщений от напарников, именованных субагентов и других сессий, с непрочитанными. <sub>рисует: полоса над полем ввода, строка статуса, панель, всплывающее уведомление, слеш-команда · автор @dot-agi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install high-command --marketplace dot-agi/high-command
  ```

  </details>
- **[İlerleme Çubuğu](https://krou4.github.io/claude-code-mod-showroom/#/mod/ilerleme-cubugu)** — Полоса прогресса над полем ввода по списку задач Claude или вашему PLAN.md, с текущим шагом (на турецком). <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @muctebadikmen · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ilerleme-cubugu --marketplace muctebadikmen/claude-code-araclari
  ```

  </details>
- **[jr awake](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-awake)** — Не даёт Mac уснуть, пока Claude работает в любой сессии, и предупреждает за минуту до сна. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-awake --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr decisions](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-decisions)** — Журнал решений по проекту: запишите решение в момент принятия, посмотрите список, выгрузите в Markdown. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-decisions --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr deslop](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-deslop)** — Отмечает приметы машинного текста в файлах, которые пишет Claude: длинные тире, «delve», штампы. <sub>рисует: всплывающее уведомление, панель, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-deslop --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr draft](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-draft)** — Черновик следующего запроса в отдельной панели, пока Claude работает; по готовности он уходит в поле ввода. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-draft --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr fleet](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-fleet)** — Все сессии Claude Code на компьютере разом: какие работают, а какие ждут вас. <sub>рисует: полоса над полем ввода, панель, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-fleet --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr goal](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-goal)** — Одна цель на проект с шагами, которые вы отмечаете; всегда видна над полем ввода со шкалой. <sub>рисует: слеш-команда, полоса над полем ввода · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-goal --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr mods](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-mods)** — Все установленные плагины и моды одним списком: отметьте несколько и примените разом. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-mods --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Launchpad](https://krou4.github.io/claude-code-mod-showroom/#/mod/launchpad)** — Кнопки в один клик для ваших команд, навыков и агентов и панель выбора модели и усилий. <sub>рисует: полоса над полем ввода, строка подсказки, панель, всплывающее уведомление, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install launchpad --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[MCP Diet](https://krou4.github.io/claude-code-mod-showroom/#/mod/mcp-diet)** — Выбор для каждого проекта, какие MCP-инструменты и типы субагентов видит Claude, с размером каждого в токенах. <sub>рисует: слеш-команда, панель · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install mcp-diet --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Mod Store](https://krou4.github.io/claude-code-mod-showroom/#/mod/mod-store)** — Панель /mods: ищите моды сообщества, смотрите, к чему они получают доступ, и ставьте после подтверждения. <sub>рисует: слеш-команда, панель, инструмент для Claude, всплывающее уведомление · автор @hellosverre · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install mod-store --marketplace hellosverre/mod-store
  ```

  </details>
- **[Model Hint](https://krou4.github.io/claude-code-mod-showroom/#/mod/model-hint)** — Подсказывает haiku, sonnet или opus для запроса, который вы печатаете, с причиной и кнопкой Switch. <sub>рисует: полоса над полем ввода, слеш-команда, строка статуса, всплывающее уведомление · автор @hashswingingslasher · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install model-hint --marketplace hashswingingslasher/model-hint
  ```

  </details>
- **[Next Steps](https://krou4.github.io/claude-code-mod-showroom/#/mod/next-steps)** — После каждого ответа над полем ввода появляются до трёх следующих запросов; 1–3 вставляет один черновиком. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @anthropics · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install next-steps --marketplace anthropics/claude-plugins-community
  ```

  </details>
- **[Noted](https://krou4.github.io/claude-code-mod-showroom/#/mod/noted)** — Когда вы поправляете Claude, предлагает короткое правило для CLAUDE.md и не плодит дубликатов. <sub>рисует: полоса над полем ввода, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install noted --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Notify](https://krou4.github.io/claude-code-mod-showroom/#/mod/notify)** — Уведомления на компьютер и телефон: долгий ход закончен, ждёт запрос разрешения или вопрос. <sub>рисует: системное уведомление, слеш-команда · автор @StanislavKozachenko · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install notify --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Oh My ClaudeAgent](https://krou4.github.io/claude-code-mod-showroom/#/mod/oh-my-claudeagent)** — Планирует вместе с вами, раздаёт задачи агентам-специалистам и не считает работу готовой без проверки. <sub>рисует: полоса над полем ввода, сообщения в переписке, панель, системное уведомление, слеш-команда · автор @UtsavBalar1231 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install oh-my-claudeagent --marketplace UtsavBalar1231/oh-my-claudeagent
  ```

  </details>
- **[Oh My Toolbelt](https://krou4.github.io/claude-code-mod-showroom/#/mod/oh-my-toolbelt)** — Панель над полем ввода: часы, погода, помидор, кнопки промптов, вложение файлов, заметки и экспорт. <sub>рисует: полоса над полем ввода, слеш-команда · автор @calmtiger86 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install oh-my-toolbelt --marketplace calmtiger86/oh-my-toolbelt
  ```

  </details>
- **[Ostrakon](https://krou4.github.io/claude-code-mod-showroom/#/mod/ostrakon)** — Панель для заметок посреди запроса; сохранённые заметки — пронумерованные чипы над полем ввода. <sub>рисует: полоса над полем ввода, инструмент для Claude, строка подсказки, слеш-команда · автор @gaius-codius · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ostrakon --marketplace gaius-codius/ostrakon
  ```

  </details>
- **[Otomatik Devir](https://krou4.github.io/claude-code-mod-showroom/#/mod/otomatik-devir)** — Делит долгую задачу на цепочку новых чатов, передающих работу у порога контекста (на турецком). <sub>рисует: строка статуса, полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @muctebadikmen · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install otomatik-devir --marketplace muctebadikmen/claude-code-araclari
  ```

  </details>
- **[Outline Sidebar](https://krou4.github.io/claude-code-mod-showroom/#/mod/outline-sidebar)** — Сессия как сворачиваемый план в боковой панели: выводы, что ждёт вас, и доказательства к каждому «сделано». <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MatsuriMW · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install outline-sidebar --marketplace MatsuriMW/outline-sidebar
  ```

  </details>
- **[Pager](https://krou4.github.io/claude-code-mod-showroom/#/mod/pager)** — Звук и уведомление, когда Claude закончил, ждёт вас или упал с ошибкой; пять наборов, mute и тихие часы. <sub>рисует: всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pager --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Pin Board](https://krou4.github.io/claude-code-mod-showroom/#/mod/pin-board)** — Постоянные заметки через /pin, которым Claude следует и после /compact и /clear, видны над полем ввода. <sub>рисует: слеш-команда, полоса над полем ввода, всплывающее уведомление · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install pin-board --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Pin Memo](https://krou4.github.io/claude-code-mod-showroom/#/mod/pin-memo)** — Закреплённые заметки и задачи с флажками над полем ввода, отдельно для каждой папки и сессии. <sub>рисует: слеш-команда, полоса над полем ввода, всплывающее уведомление · автор @YeonwooSung · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pin-memo --marketplace YeonwooSung/my-claude-code-mods
  ```

  </details>
- **[Pinboard](https://krou4.github.io/claude-code-mod-showroom/#/mod/pinboard)** — Доска с решениями, задачами и ссылками рядом с чатом; Claude закрепляет их своим инструментом. <sub>рисует: инструмент для Claude, панель, полоса над полем ввода, слеш-команда · автор @timoncool · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install pinboard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Pins](https://krou4.github.io/claude-code-mod-showroom/#/mod/pins)** — Закреплённые указания переживают сжатие, /clear и перезапуск; каждый запрос передаёт их Claude. <sub>рисует: слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pins --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Plan Checklist](https://krou4.github.io/claude-code-mod-showroom/#/mod/plan-checklist)** — Одобренный план становится чек-листом над полем ввода; Claude отмечает шаг только с доказательством проверки. <sub>рисует: инструмент для Claude, полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @Jh-jaehyuk · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install plan-checklist --marketplace Jh-jaehyuk/plan-checklist
  ```

  </details>
- **[Pop Quiz](https://krou4.github.io/claude-code-mod-showroom/#/mod/pop-quiz)** — Два коротких вопроса о последней правке Claude над полем ввода, ответ на каждый открывается одним нажатием. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pop-quiz --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Porthole](https://krou4.github.io/claude-code-mod-showroom/#/mod/porthole)** — Скриншот вашего локального dev-сервера в панели рядом с чатом, обновляется после правок Claude. <sub>рисует: всплывающее уведомление, панель, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install porthole --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Prompt Lift](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-lift)** — Enhance, Send и Undo над полем ввода: размытый черновик переписывается по инструкциям вашего проекта. <sub>рисует: переписывание промпта, полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @sairam0424 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install prompt-lift --marketplace sairam0424/claude-prompt-lift
  ```

  </details>
- **[Prompt Polish](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-polish)** — Переписывает запрос по гайду для модели сессии и спрашивает, какой вариант отправить. <sub>рисует: переписывание промпта, панель, слеш-команда · автор @jheroorehj · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install prompt-polish --marketplace jheroorehj/prompt-polish
  ```

  </details>
- **[Prompt Snippets](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-snippets)** — Сохраните промпт один раз, вставляйте его через /snip, а выделение цитируйте через /quote. <sub>рисует: слеш-команда · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install prompt-snippets --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Rain Check](https://krou4.github.io/claude-code-mod-showroom/#/mod/rain-check)** — Упёрлись в лимит? Отправленный запрос подождёт и уйдёт сам, когда лимит сбросится. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install rain-check --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Red Green](https://krou4.github.io/claude-code-mod-showroom/#/mod/red-green)** — Запускает тесты после каждого хода с правками и пишет итог; /fix отправляет ошибку обратно Claude. <sub>рисует: сообщения в переписке, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install red-green --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Replay Theater](https://krou4.github.io/claude-code-mod-showroom/#/mod/replay-theater)** — Пролистайте правки файлов за последний ход в панели, по одному красно-зелёному диффу за шаг. <sub>рисует: слеш-команда, панель · автор @anthropics · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install replay-theater --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Reply Choices](https://krou4.github.io/claude-code-mod-showroom/#/mod/reply-choices)** — Пронумерованные варианты в конце ответа Claude превращаются в кнопки над полем ввода. <sub>рисует: полоса над полем ввода · автор @timoncool · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install reply-choices --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Right Tool](https://krou4.github.io/claude-code-mod-showroom/#/mod/right-tool)** — Отклоняет простые cat, head, sed -n, grep и find в Bash и подсказывает точный вызов Read, Grep или Glob. <sub>рисует: блокировка инструментов, строки инструментов, сообщения в переписке, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install right-tool --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Snippets](https://krou4.github.io/claude-code-mod-showroom/#/mod/snippets)** — Сохранённые запросы попадают в поле ввода с подставленной веткой, выделением и вашим текстом. <sub>рисует: слеш-команда, всплывающее уведомление · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install snippets --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Standup](https://krou4.github.io/claude-code-mod-showroom/#/mod/standup)** — Записывает каждый ход в журнал и одной командой пишет стендап: вчера, сегодня, блокеры. <sub>рисует: слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install standup --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Suggest](https://krou4.github.io/claude-code-mod-showroom/#/mod/suggest)** — Вероятные ответы кнопками под последним сообщением Claude: щёлкните, чтобы отправить. <sub>рисует: сообщения в переписке, строка статуса, слеш-команда · автор @dophamine · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install suggest --marketplace dophamine/claude-suggest
  ```

  </details>
- **[Swiss Knife](https://krou4.github.io/claude-code-mod-showroom/#/mod/swiss-knife)** — Сигнал, когда Claude ждёт вас, шкалы лимитов с прогнозом и передача дел в новый чат. <sub>рисует: полоса над полем ввода, системное уведомление, панель, строка статуса, всплывающее уведомление, слеш-команда · автор @nocodehack · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install swiss-knife --marketplace nocodehack/swiss-knife
  ```

  </details>
- **[Synaptik](https://krou4.github.io/claude-code-mod-showroom/#/mod/synaptik)** — Принимайте, отклоняйте или комментируйте любую часть ответа Claude; пометки собираются в один запрос. <sub>рисует: полоса над полем ввода, строка подсказки, панель, всплывающее уведомление, слеш-команда · автор @synaptik-app · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install synaptik --marketplace synaptik-app/synaptik
  ```

  </details>
- **[Term Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/term-bar)** — Кнопки в нижней строке терминала: вернуться к недавнему разговору, выбрать модель и уровень усилий. <sub>рисует: полоса над полем ввода, метка режима, всплывающее уведомление · автор @hyun8935181-ux · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install term-bar --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Test HUD](https://krou4.github.io/claude-code-mod-showroom/#/mod/test-hud)** — Пройдено из общего на строке подсказки после каждого прогона, падения по файлам и сигнал о нестабильных. <sub>рисует: строка подсказки, панель, всплывающее уведомление, строка статуса, слеш-команда · автор @ice-lfernandes · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install test-hud --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[TL;DR](https://krou4.github.io/claude-code-mod-showroom/#/mod/tldr)** — Краткое резюме в одно предложение под каждым длинным ответом, его пишет небольшая быстрая модель. <sub>рисует: сообщения в переписке, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install tldr --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Topic Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/topic-guard)** — Придерживает сообщение на новую тему: можно отправить его в новую сессию или оставить здесь. <sub>рисует: полоса над полем ввода, строка статуса, всплывающее уведомление · автор @dougcunha · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install topic-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Watch Command](https://krou4.github.io/claude-code-mod-showroom/#/mod/watch-command)** — /watch перезапускает команду по таймеру и показывает в строке состояния, проходит ли она. <sub>рисует: слеш-команда, строка статуса, всплывающее уведомление · автор @timoncool · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install watch-command --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Word Predict](https://krou4.github.io/claude-code-mod-showroom/#/mod/word-predict)** — Подсказки слов как на клавиатуре телефона: дописать слово или взять следующее через Option+1/2/3. <sub>рисует: полоса над полем ввода, слеш-команда, всплывающее уведомление, строка статуса · автор @tehwave · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install word-predict --marketplace tehwave/claude-word-predict
  ```

  </details>

### Git

- **[Change Ledger](https://krou4.github.io/claude-code-mod-showroom/#/mod/change-ledger)** — Панель /changes со всеми файлами, которые правила сессия: сколько строк, кто правил, и рядом git. <sub>рисует: панель, слеш-команда · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install change-ledger --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Changes](https://krou4.github.io/claude-code-mod-showroom/#/mod/changes)** — Лента по ходам: что изменил Claude, дифф по каждому файлу и кнопки Keep или Revert. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @candygoogy · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install changes --marketplace candygoogy/notary
  ```

  </details>
- **[Chapters](https://krou4.github.io/claude-code-mod-showroom/#/mod/chapters)** — /chapters превращает дифф в главы ревью с отметками риска и показывает их в панели рядом с изменениями. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install chapters --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[CI Budget](https://krou4.github.io/claude-code-mod-showroom/#/mod/ci-budget)** — Минуты, расходы и бюджет GitHub Actions на виду, пока Claude пишет workflow и пушит. <sub>рисует: строка статуса, всплывающее уведомление, слеш-команда, блокировка инструментов · автор @StanislavKozachenko · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ci-budget --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[CI Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/ci-watch)** — После push или PR от Claude запуски GitHub Actions видны над полем ввода с полосой, затем успех или провал. <sub>рисует: полоса над полем ввода, всплывающее уведомление · автор @arasovic · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install ci-watch --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[GH Status](https://krou4.github.io/claude-code-mod-showroom/#/mod/gh-status)** — Pull request вашей ветки вживую: проверки, ревью, обсуждения, очередь слияния и слияние с подтверждением. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда · автор @oborchers · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install gh-status --marketplace oborchers/claude-gh-status
  ```

  </details>
- **[Git Glance](https://krou4.github.io/claude-code-mod-showroom/#/mod/git-glance)** — Ветка, изменённые файлы и коммиты впереди или позади upstream в строке статуса под полем ввода. <sub>рисует: строка статуса · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install git-glance --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Git Pulse](https://krou4.github.io/claude-code-mod-showroom/#/mod/git-pulse)** — Ветка, опережение и отставание, конфликты, staged, изменённые и неотслеживаемые файлы под полем ввода. <sub>рисует: строка статуса, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install git-pulse --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[jr commit coach](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-commit-coach)** — Когда незакоммиченных правок становится слишком много, полоса и уведомление предлагают разбить их по папкам. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-commit-coach --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[PR Inbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/pr-inbox)** — Запросы на ревью и ваши PR как входящие: оценка риска, AI-ревью, слияние и исправление CI. <sub>рисует: строка статуса, панель, всплывающее уведомление, слеш-команда · автор @2bo · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pr-inbox --marketplace 2bo/pr-inbox
  ```

  </details>
- **[PR Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/pr-watch)** — Живая панель GitHub PR, которые сессия открыла или куда пушила: CI, ревью, конфликты и слияние. <sub>рисует: панель, всплывающее уведомление, строка статуса, слеш-команда, инструмент для Claude · автор @ElirazKed · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pr-watch --marketplace ElirazKed/claude-code-pr-watch
  ```

  </details>
- **[Review Inbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/review-inbox)** — PR, которые ждут вашего ревью, с понятным кратким пересказом, а также ваши PR и задачи. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда, инструмент для Claude · автор @SummerRiversound · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install review-inbox --marketplace SummerRiversound/review-inbox
  ```

  </details>
- **[Split Diff View](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-split-diff-view)** — Диффы Edit и Write в две колонки рядом, а /diffsplit показывает так же все незакоммиченные изменения. <sub>рисует: строки инструментов, слеш-команда, панель · автор @neteye-platform · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cc-split-diff-view --marketplace neteye-platform/cc-split-diff-view
  ```

  </details>
- **[Visual Review](https://krou4.github.io/claude-code-mod-showroom/#/mod/visual-review)** — /visual-review рисует дизайн изменений ветки диаграммой в браузере; комментарии уходят обратно в сессию. <sub>рисует: слеш-команда, инструмент для Claude, всплывающее уведомление, строка статуса · автор @dougcunha · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install visual-review --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Worktrees](https://krou4.github.io/claude-code-mod-showroom/#/mod/worktrees)** — Каждый агент, который правит код, получает свой git worktree от вашего коммита и убирается после слияния. <sub>рисует: всплывающее уведомление, слеш-команда · автор @AbhiramDwivedi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install worktrees --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>

### Интеграции

- **[Agent Mobile Observer](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-mobile-observer)** — Спутник сервера agent-mobile-control для чата с телефона: сообщает ему о начале и конце ходов локально. <sub>автор @Coolkidlab-Yin · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install agent-mobile-observer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Buddy Chat](https://krou4.github.io/claude-code-mod-showroom/#/mod/buddy-chat)** — Чат со сквозным шифрованием с другими пользователями Claude Code в панели, через ретранслятор ntfy.sh. <sub>рисует: панель, инструмент для Claude, строка статуса, всплывающее уведомление, системное уведомление, слеш-команда · автор @MrMirhan · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install buddy-chat --marketplace MrMirhan/claude-buddy-chat
  ```

  </details>
- **[Cactus Pane](https://krou4.github.io/claude-code-mod-showroom/#/mod/cactus-pane)** — Вопросы агента из cactus в боковой панели: отвечаете прямо там, и агент получает ответ. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @eighteyes · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install cactus-pane --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[CodeBuild](https://krou4.github.io/claude-code-mod-showroom/#/mod/codebuild)** — Сборка репозитория в AWS CodeBuild прямо из Claude Code: выберите профиль, нажмите Build и следите за ходом. <sub>рисует: панель, строка статуса, всплывающее уведомление, слеш-команда, инструмент для Claude · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install codebuild --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Desk Asana](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-asana)** — Ваши задачи из Asana в боковой панели: по проектам, поиск, подробности, комментарии, исполнитель и статус. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @KyongSik-Yoon · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install desk-asana --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Desk Slack](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-slack)** — Личные сообщения из Slack как переписки в боковой панели: с ответами и уведомлениями о новых. <sub>рисует: слеш-команда, панель, системное уведомление, всплывающее уведомление · автор @KyongSik-Yoon · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install desk-slack --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Editor Context](https://krou4.github.io/claude-code-mod-showroom/#/mod/editor-context)** — Файл и выделение из Cursor или VS Code над полем ввода, которые уходят Claude с каждым сообщением. <sub>рисует: полоса над полем ввода, слеш-команда · автор @talbarina · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install editor-context --marketplace talbarina/claude-editor-context
  ```

  </details>
- **[RoadRaven HUD](https://krou4.github.io/claude-code-mod-showroom/#/mod/roadraven-hud)** — Живая панель для приложения-роадмапа RoadRaven: агенты на узлах, приёмка Pass/Fail и бэклог для запуска. <sub>рисует: строка статуса, панель, всплывающее уведомление, слеш-команда · автор @Shuffzord · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install roadraven-hud --marketplace Shuffzord/RoadRaven
  ```

  </details>
- **[Standby](https://krou4.github.io/claude-code-mod-showroom/#/mod/standby)** — Расшифровка встреч и голосовые звонки из Mac-приложения Standby, с живой полосой над полем ввода. <sub>рисует: полоса над полем ввода, сообщения в переписке, всплывающее уведомление, слеш-команда, инструмент для Claude · автор @mksadoughi · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install standby --marketplace mksadoughi/standby
  ```

  </details>
- **[Wirepane](https://krou4.github.io/claude-code-mod-showroom/#/mod/wirepane)** — HTTPS-прокси для отладки в панели; Claude читает, повторяет и подменяет трафик вашего приложения. <sub>рисует: панель, инструмент для Claude, строка статуса, всплывающее уведомление, слеш-команда · автор @legostin · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install wirepane --marketplace legostin/wirepane
  ```

  </details>

### Для настроения

- **[2048](https://krou4.github.io/claude-code-mod-showroom/#/mod/game-2048)** — 2048 в боковой панели: плитки двигаются клавишами w a s d, две отмены хода и рекорд, который не сбрасывается. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install game-2048 --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[ASCII Dungeon](https://krou4.github.io/claude-code-mod-showroom/#/mod/ascii-dungeon)** — Пиксельный рогалик в панели, в который играет ваша сессия: каждый вызов инструмента двигает героя. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @ilovepixelart · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install ascii-dungeon --marketplace ilovepixelart/ascii-dungeon-mod
  ```

  </details>
- **[Bingo](https://krou4.github.io/claude-code-mod-showroom/#/mod/bingo)** — Бинго на 75 шаров против Claude в панели: вызывайте числа, отмечайте карточку и кричите «Бинго» первым. <sub>рисует: слеш-команда, панель, всплывающее уведомление · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install bingo --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Boss Fight](https://krou4.github.io/claude-code-mod-showroom/#/mod/boss-fight)** — Упавшие тесты вызывают пиксельного босса с 1 HP за каждый провал; каждый прогон с исправлениями бьёт его. <sub>рисует: панель, всплывающее уведомление, строка статуса, слеш-команда · автор @OneWave-AI · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install boss-fight --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Brainrot Break](https://krou4.github.io/claude-code-mod-showroom/#/mod/brainrot-break)** — Лента в стиле TikTok из 450+ пиксельных мини-видео, которую можно листать, пока Claude отвечает. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @BordyV · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install brainrot-break --marketplace BordyV/brainrot-break
  ```

  </details>
- **[Brickfall](https://krou4.github.io/claude-code-mod-showroom/#/mod/brickfall)** — Яркий арканоид в панели: ракетка за мышью, капсулы с бонусами и цепные взрывы вольт-кирпичей. <sub>рисует: панель, слеш-команда · автор @reporails · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install brickfall --marketplace reporails/arcade
  ```

  </details>
- **[Buddy](https://krou4.github.io/claude-code-mod-showroom/#/mod/buddy)** — ASCII-питомец над полем ввода: реагирует на инструменты Claude, радуется зелёным тестам и растёт в уровнях. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install buddy --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Cat Spinner](https://krou4.github.io/claude-code-mod-showroom/#/mod/cat-spinner)** — Пиксельный кот гуляет над спиннером, садится подумать и реагирует на инструменты Claude. <sub>рисует: слеш-команда, панель, спиннер · автор @swicken · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cat-spinner --marketplace swicken/cat-spinner
  ```

  </details>
- **[Claudinho](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudinho)** — Футбол в прямом эфире для вашего турнира: счёт или отсчёт до матча над полем ввода, уведомления о голах. <sub>рисует: полоса над полем ввода, всплывающее уведомление, панель, слеш-команда · автор @arturogarrido · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install claudinho --marketplace arturogarrido/claudinho
  ```

  </details>
- **[Clawd Pet](https://krou4.github.io/claude-code-mod-showroom/#/mod/clawd-pet)** — Пиксельный Clawd над полем ввода: показывает текущий инструмент, радуется пройденным тестам и спит в простое. <sub>рисует: полоса над полем ввода, слеш-команда · автор @Revono · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install clawd-pet --marketplace Revono/clawd-pet
  ```

  </details>
- **[Code Pet](https://krou4.github.io/claude-code-mod-showroom/#/mod/code-pet)** — Пиксельный питомец на панели: ест при вызовах инструментов, болеет от ошибок и паникует от rm -rf. <sub>рисует: слеш-команда, панель, строка статуса, всплывающее уведомление · автор @OneWave-AI · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install code-pet --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Connect Four](https://krou4.github.io/claude-code-mod-showroom/#/mod/connect-four)** — «Четыре в ряд» против Claude в боковой панели: три уровня, от простого до просчёта на семь ходов. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install connect-four --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Fables](https://krou4.github.io/claude-code-mod-showroom/#/mod/fables)** — Мультфильм над полем ввода: Sonnet или Haiku пересказывает вызовы инструментов и реплики сценами с подписями. <sub>рисует: полоса над полем ввода, слеш-команда · автор @henrik-thevibe · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install fables --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Halftime](https://krou4.github.io/claude-code-mod-showroom/#/mod/halftime)** — Четыре маленькие игры над полем ввода, пока Claude работает; свисток ставит игру на паузу, когда нужны вы. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install halftime --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Hatchling](https://krou4.github.io/claude-code-mod-showroom/#/mod/hatchling)** — Коллекционный пиксельный питомец над полем ввода: после 25 вызовов из яйца вылупляется один из 9 видов. <sub>рисует: полоса над полем ввода, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install hatchling --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Hero Journey](https://krou4.github.io/claude-code-mod-showroom/#/mod/hero-journey)** — Уютный RPG-интерфейс: крабы Clawd разных классов изображают инструменты, есть панель квестов и итог хода. <sub>рисует: строки инструментов, строка длительности хода, спиннер, полоса над полем ввода, панель, слеш-команда · автор @soulrocha · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install hero-journey --marketplace soulrocha/Claude-code-hero-journey
  ```

  </details>
- **[Mindful Breathing](https://krou4.github.io/claude-code-mod-showroom/#/mod/mindful-breathing)** — Пока Claude работает, над полем ввода идёт дыхательное упражнение, а спиннер отсчитывает фазы дыхания. <sub>рисует: полоса над полем ввода, спиннер, слеш-команда · автор @halluton · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install mindful-claude --marketplace halluton/Mindful-Claude
  ```

  </details>
- **[Minefield](https://krou4.github.io/claude-code-mod-showroom/#/mod/minefield)** — Сапёр в панели: разминируйте поле 9×9 мышью или клавишами, пока Claude работает. <sub>рисует: панель, слеш-команда · автор @reporails · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install minefield --marketplace reporails/arcade
  ```

  </details>
- **[miod](https://krou4.github.io/claude-code-mod-showroom/#/mod/miod)** — Своя мелодия для каждой задачи, сочинённая на лету; настроение задают действия агента и темп расхода токенов. <sub>рисует: полоса над полем ввода, слеш-команда, всплывающее уведомление · автор @delexw · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install miod --marketplace delexw/miod
  ```

  </details>
- **[Pairs](https://krou4.github.io/claude-code-mod-showroom/#/mod/pairs)** — Игра на память в боковой панели: шестнадцать карт рубашкой вверх, восемь пар, рекорды по ходам и времени. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pairs --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Pixel Fishing](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixel-fishing)** — 8-битный рыбак в боковой панели забрасывает спиннинг, пока Claude работает, и вываживает рыбу с ответом. <sub>рисует: панель, слеш-команда · автор @s7788 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pixel-fishing --marketplace s7788/pixel-fishing
  ```

  </details>
- **[Pixel Hunter](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixel-hunter)** — 8-битный охотник сражается с одним из девяти монстров в боковой панели, пока Claude работает. <sub>рисует: панель, слеш-команда · автор @s7788 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pixel-hunter --marketplace s7788/pixel-hunter
  ```

  </details>
- **[Pixpal](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixpal)** — Пиксельный приятель над полем ввода разыгрывает инструменты Claude и реагирует на каждый ответ. <sub>рисует: полоса над полем ввода, панель, всплывающее уведомление, слеш-команда · автор @castus · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install pixpal --marketplace castus/pixpal
  ```

  </details>
- **[Second Wind](https://krou4.github.io/claude-code-mod-showroom/#/mod/second-wind)** — Пока Claude работает, над полем ввода дыхание, отдых для глаз 20-20-20 или разминка, по длине ожидания. <sub>рисует: полоса над полем ввода, спиннер, строка статуса, всплывающее уведомление, слеш-команда · автор @modmyclaude · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install second-wind --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Slapbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/slapbox)** — Отшлёпайте мультяшную попку над полем ввода, когда Claude накосячил; он узнает счёт с сообщением. <sub>рисует: полоса над полем ввода, слеш-команда · автор @timoncool · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install slapbox --marketplace timoncool/slapbox
  ```

  </details>
- **[Snake](https://krou4.github.io/claude-code-mod-showroom/#/mod/snake)** — «Змейка» в боковой панели: управление w a s d, ешьте еду, пауза на p, выбор скорости и рекорд. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install snake --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Spinner Pack](https://krou4.github.io/claude-code-mod-showroom/#/mod/spinner-pack)** — Тематический спиннер: луна, шрифт Брайля или кофе; слово и значок меняются с каждой фазой хода. <sub>рисует: спиннер · автор @KROU4 · в этом репозитории</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install spinner-pack --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Spinner Packs](https://krou4.github.io/claude-code-mod-showroom/#/mod/spinner-packs)** — Десять тематических наборов слов для индикатора работы, от пиратского до нуара; итог хода в прошедшем времени. <sub>рисует: спиннер, строка длительности хода, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install spinner-packs --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Storytime](https://krou4.github.io/claude-code-mod-showroom/#/mod/storytime)** — Крошечный локальный трансформер печатает над полем ввода сказку о том, чем сейчас занят Claude. <sub>рисует: полоса над полем ввода, слеш-команда · автор @maddiedreese · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install storytime --marketplace maddiedreese/cc-storytime
  ```

  </details>
- **[Sudoku](https://krou4.github.io/claude-code-mod-showroom/#/mod/sudoku)** — Судоку в боковой панели: три уровня с единственным решением, отмена, подсказки и лучшее время по уровням. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @MDmubarak786 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install sudoku --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Terminal Gym](https://krou4.github.io/claude-code-mod-showroom/#/mod/terminal-gym)** — Дневная норма повторений над полем ввода: отмечайте подходы кнопками +5/+10/+25 и держите серию дней. <sub>рисует: полоса над полем ввода, спиннер, всплывающее уведомление, слеш-команда, панель · автор @DrumAndCode · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install terminal-gym --marketplace DrumAndCode/terminal-gym
  ```

  </details>
- **[textless](https://krou4.github.io/claude-code-mod-showroom/#/mod/textless)** — Пока Claude работает, вместо ленты шагов в чате стоит одна карточка с пиксельной картинкой. <sub>рисует: строки инструментов, слеш-команда · автор @HeyCubit · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install textless --marketplace HeyCubit/effortless
  ```

  </details>
- **[Verbs](https://krou4.github.io/claude-code-mod-showroom/#/mod/verbs)** — Пока Claude работает, над спиннером крутится пиксельная картинка его глагола, своя для каждого из 188. <sub>рисует: слеш-команда, спиннер, всплывающее уведомление · автор @olliewagner · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install verbs --marketplace olliewagner/verbs
  ```

  </details>
- **[Wrapped](https://krou4.github.io/claude-code-mod-showroom/#/mod/wrapped)** — Годовой итог работы с Claude Code: статистика, серии дней, ваш «типаж» и карточка, чтобы поделиться. <sub>рисует: панель, всплывающее уведомление, слеш-команда · автор @Singh-AP · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install wrapped --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>

### Доступность

- **[jr dictation](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-dictation)** — Исправляет ошибки диктовки («type script» → TypeScript) до того, как Claude прочтёт запрос. <sub>рисует: переписывание промпта, сообщения в переписке, слеш-команда · автор @jrlprost · внешний</sub>
  <details><summary>Установка</summary>

  ```text
  /plugin install jr-dictation --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[RTL Terminal](https://krou4.github.io/claude-code-mod-showroom/#/mod/rtl-terminal)** — Ответы на арабском, иврите, фарси и урду выводятся справа налево, маркеры списков — справа. <sub>рисует: сообщения в переписке, полоса над полем ввода, слеш-команда · автор @MohammedSaud404 · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install rtl-terminal --marketplace MohammedSaud404/rtl-terminal
  ```

  </details>
- **[Simplified Chinese UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-zh)** — Слэш-команды, строки /config, индикатор работы, подсказки и уведомления Claude Code на упрощённом китайском. <sub>рисует: спиннер, строки инструментов, строка длительности хода, строка подсказки, слеш-команда, всплывающее уведомление · автор @jiangnanquan · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install cc-zh --marketplace jiangnanquan/claude-code-zh
  ```

  </details>
- **[TTS](https://krou4.github.io/claude-code-mod-showroom/#/mod/tts)** — Читает ответы Claude вслух по предложению прямо во время вывода через VOICEVOX, Irodori-TTS или команду. <sub>рисует: слеш-команда, панель, строка статуса, всплывающее уведомление · автор @kajidog · внешний</sub>
  <details><summary>Установка (из маркетплейса автора)</summary>

  ```text
  /plugin install tts --marketplace kajidog/cc-mods-tts
  ```

  </details>
<!-- mods:end -->

## Добавить свой мод

Каталог открыт для всех. Запись — это один файл `mods/<имя>/mod.json`: название, описание, откуда ставить и превью для сайта. Добавить её можно тремя способами:

1. **Конструктор на сайте** ([Submit a mod](https://krou4.github.io/claude-code-mod-showroom/#/submit)): заполните форму, посмотрите превью и откройте pull request одной кнопкой.
2. **Через веб-интерфейс GitHub**: Add file → Create new file → `mods/<имя>/mod.json`.
3. **Через git**: форк, файл, `npm ci && npm run check`, pull request.

Код мода может лежать в вашем репозитории (`source: github`) или прямо здесь, в `mods/<имя>/plugin/`. Если все изменения внутри `mods/<имя>/`, проверки прошли и вы указаны в `maintainers`, бот сольёт запрос сам. Подробности в [CONTRIBUTING.md](CONTRIBUTING.md), формат превью в [docs/preview-dsl.md](docs/preview-dsl.md).

## Как защищён репозиторий

- Ветку `main` нельзя удалить или переписать: удаление и force-push запрещены без исключений, даже для администратора.
- Изменения попадают в `main` только через pull request.
- Бот сливает запрос сам, только если все файлы внутри `mods/<имя>/`, проверка Validate прошла для этого самого коммита, автор — мейнтейнер изменённых записей (у новой записи — указан в `maintainers`), а поле `verified` не тронуто. Код и `source` модов, которые уже есть в каталоге, он не меняет: это читает мейнтейнер. Остальное тоже смотрит мейнтейнер.
- Бот не запускает код из pull request с правами на запись: он читает запрос через GitHub API как данные.
- Ошибку исправляют новым коммитом (revert), история не переписывается.

Полная модель — в [docs/governance.md](docs/governance.md). Как сообщить о вредном моде — в [SECURITY.md](SECURITY.md).

## Исследование

[docs/research.md](docs/research.md): как устроены моды, где и что они рисуют, какие есть способы установки и ссылки для запуска, какие каталоги модов уже существуют и чем этот отличается.

## Связанные проекты

Другие места, где искать моды. Список взят из нашего исследования экосистемы в октябре 2026 года.

**Каталоги и индексы**

- [Awesome Claude Code Mods](https://github.com/karanb192/awesome-claude-code-mods) — самый большой индекс модов: автоматический скан GitHub, `claude plugin validate` для каждого мода, оценка доступа; сайт [mods.aidojo.si](https://mods.aidojo.si/).
- [statuslin.es](https://statuslin.es/mods) — курируемая галерея; превью записаны из настоящего Claude Code и Claude Desktop.
- [claudemods.chat](https://claudemods.chat) — каталог и маркетплейс из одного файла данных, каждый мод закреплён на проверенном коммите.
- [claude-mods.com](https://claude-mods.com/) — ежедневный скан GitHub с ручной проверкой и метками поверхностей.
- [modsforClaude](https://modsforclaude.com/) — фильтры по категориям и типам хуков, ревью привязано к коммиту.
- [Claude Mods](https://claudemods.ai/) — ручная модерация, голосование за мод дня, JSON-фид.
- [CCMods Hub](https://ccmodshub.com/) — галерея модов по разделам.
- [slopshopper](https://github.com/ryx2/slopshopper) — ежедневный скан GitHub и превью из прогона мода на имитации API.
- [awesome-claude-mods](https://github.com/wh000wh000/awesome-claude-mods) — индекс, где у каждого мода указано, чем подтверждены данные; обновляется каждые два часа.

**Маркетплейсы и коллекции**

- [baselane-sh/mods-catalog](https://github.com/baselane-sh/mods-catalog) — маркетплейс с источниками, закреплёнными по коммиту; запись добавляется одним pull request.
- [whyashthakker/awesome-claude-code-mods](https://github.com/whyashthakker/awesome-claude-code-mods) — собственные моды с тестами и скриншотами из тестового набора Claude Code.
- [hamzafer/claude-code-mods](https://hamzafer.github.io/claude-code-mods/) — моды по категориям со скриншотами.
- [Plagemes/claude-mods](https://plagemes.github.io/claude-mods/) — собственные моды и магазин внутри терминала.
- [Mod Store](https://github.com/hellosverre/mod-store) — магазин модов прямо в клиенте: панель `/mods` с поиском и установкой.

**От Anthropic**

- [Документация по модам](https://code.claude.com/docs/en/plugins/mods/overview) — обзор, справочник, API, тесты, администрирование.
- [Встроенные моды](https://github.com/anthropics/claude-code/tree/main/mods) — исходники модов, которые поставляются с Claude Code.
- [Моды из claude-code-playground](https://github.com/anthropics/claude-code-playground/tree/main/claude-code/mods) — демонстрационные моды со скриншотами.

**Списки**

- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) — большой список ресурсов по Claude Code с разделом Mods.

## Лицензия

Каталог, скрипты, сайт и моды из `mods/*/plugin/` распространяются по лицензии [MIT](LICENSE). Внешние моды остаются под лицензиями своих авторов (поле `license` в записи).

Это проект сообщества. Он не связан с Anthropic и не одобрен ею. Claude и Claude Code — товарные знаки Anthropic.
