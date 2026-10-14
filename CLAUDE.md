# Портал Баня-МСК — тестовый репозиторий

`test.portal.baniamsk.ru`. Боевой — `kislitsynkonstantin/portal` (`portal.baniamsk.ru`).
План, решения и статус шагов — `docs/portal-plan.md` в `kislitsynkonstantin/claude-workspace`.

## Главное правило: в репозитории нет данных

Репозиторий публичный, GitHub Pages публичен даже из приватного репозитория. Здесь лежит только оболочка
страницы: ни сумм, ни названий проектов, ни имён контрагентов — ни в файлах, ни в истории git.
Данные приходят после входа из Supabase (`portal_objects()`, `portal_users()`) под RLS.
Перед каждым пушем проверить: в `index.html` нет номеров проектов (`#5…`) и фамилий контрагентов.

## Как собирается

`index.html` не правится руками: его собирает `bmsk-dashboard-builder/build_portal.py` в `claude-workspace`
из стилей и скриптов дашборда (`_css*.txt`, `_js*.txt`) и файлов `portal/portal.js`, `portal/portal.css`.

## Ведение — как у калькулятора

- Одна ветка `main`.
- Версия — `PORTAL_VERSION` в `config.py` сборщика, формат `v{версия} ({счётчик})`; бейдж на странице и в журнале.
- Журнал — `docs/CHANGELOG.md`, верхний раздел открытый, смысл правки, а не список файлов.
- Цикл: правка → проверка в Chromium (390 / 768 / 1440, обе темы, Supabase подменяется заглушкой) → пуш сюда →
  Константин смотрит на test.portal → «выкладываем» → копия в `portal` → portal.baniamsk.ru.
