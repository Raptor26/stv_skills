# Пользовательские skills для Kimi Code

В этом репозитории хранятся собственные skills для [Kimi Code](https://moonshotai.github.io/kimi-code/).

## Структура репозитория

Каждый skill — это отдельный подкаталог с файлом `SKILL.md`:

```text
stv/skills/
  git-commiting-russian/
    SKILL.md
  ...
```

Файл `SKILL.md` должен содержать YAML frontmatter с обязательными полями `name` и `description`:

```markdown
---
name: git-commiting-russian
description: "Создает сообщение фиксации на русском языке согласно стилю commitizen"
---

# Название skill
...
```

Имя skill должно состоять только из букв, цифр и дефисов.

## Подключение к Kimi Code

Kimi Code не сканирует этот репозиторий автоматически, потому что он расположен в нестандартном каталоге. Чтобы skills стали доступны, нужно добавить путь к репозиторию в конфигурацию.

Откройте файл `~/.kimi-code/config.toml` и добавьте (или измените) параметр `extra_skill_dirs`:

```toml
extra_skill_dirs = ["/Users/raptor/.kimi-code/stv/skills"]
```

Если у вас уже указаны другие дополнительные директории, добавьте путь через запятую:

```toml
extra_skill_dirs = ["/path/to/other/skills", "/Users/raptor/.kimi-code/stv/skills"]
```

## Применение изменений

После сохранения `config.toml` **перезапустите Kimi Code** (завершите текущую сессию и запустите `kimi` заново). Skills загружаются при старте сессии.

## Альтернативный способ

Можно указать директорию skills один раз при запуске, не изменяя конфиг:

```bash
kimi --skills-dir /Users/raptor/.kimi-code/stv/skills
```

## Использование skill

После подключения skill вызывается по имени из YAML frontmatter через инструмент `Skill`. Например:

```text
Skill: git-commiting-russian
```

## Добавление нового skill

1. Создайте подкаталог с именем skill.
2. Добавьте в него файл `SKILL.md` с корректным frontmatter.
3. Перезапустите Kimi Code, чтобы он подхватил изменения.
