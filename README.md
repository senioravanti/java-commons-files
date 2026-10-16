# Утилиты для работы с файлами

## Загрузка релиза на github

`go install github.com/sibprogrammer/xq@latest` :: Установить [xq](https://github.com/sibprogrammer/xq)

`sudo pacman -Sy github-cli` :: Установить [gh](https://github.com/cli/cli)

Нужно создать токен с scope: `repo`, `read:org`, `admin:public_key`
`gh auth login`

`go install github.com/mikefarah/yq/v4@latest` :: Установить [yq](https://github.com/mikefarah/yq)

```sh
version="$(yq '.settings.publishing.version' module.yaml)"
git tag -m '' "v${version}" main
git push --follow-tags origin main
gh release create "v${version}" \
  --target main \
  --notes-from-tag \
  --title "${version}"
```

`git push --tags` :: Отправить все теги в удалённый репозиторий.
`git tag -l` :: Список тэгов
`git tag -d <tag>` :: Удалить тэг `<tag>` локально.
`git push origin :refs/tags/<tag>` :: Удалить тэг `<tag>` в удалённом репозитории.
