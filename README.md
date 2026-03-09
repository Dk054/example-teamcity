<img width="1647" height="954" alt="Снимок экрана 2026-03-09 135626" src="https://github.com/user-attachments/assets/933e8801-a159-4b84-9102-1d13e0de0219" /># Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](Ansible/infrastructure).

## Основная часть

1. Создайте новый проект в teamcity на основе fork.
<img width="1861" height="788" alt="Снимок экрана 2026-03-09 112828" src="https://github.com/user-attachments/assets/97d275e9-da3f-49ff-bc65-4f4839acbe75" />
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.
<img width="1768" height="783" alt="Снимок экрана 2026-03-09 114032" src="https://github.com/user-attachments/assets/92f3d628-35a6-4cd1-8c9f-bdcab628c203" />
4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.
<img width="1859" height="799" alt="Снимок экрана 2026-03-09 115012" src="https://github.com/user-attachments/assets/da5f2d5a-bc73-44ba-8c58-ed342390613d" />
5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
<img width="1757" height="891" alt="Снимок экрана 2026-03-09 115909" src="https://github.com/user-attachments/assets/d03ef6a1-de95-4212-a72e-9e549a07770d" />
8. Мигрируйте `build configuration` в репозиторий.
<img width="1647" height="954" alt="Снимок экрана 2026-03-09 135626" src="https://github.com/user-attachments/assets/b26c38b4-9ca0-4d81-a1af-39cdb7ab6fe7" />
9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
<img width="1655" height="984" alt="Снимок экрана 2026-03-09 140539" src="https://github.com/user-attachments/assets/bbd16ca1-52f5-4528-833b-1d0e416cf0fa" />
14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.
15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`. сборки не было
16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.
<img width="1341" height="790" alt="Снимок экрана 2026-03-09 141119" src="https://github.com/user-attachments/assets/bb4719c9-aa6e-4db7-884e-b53c687c9ddd" />
17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
<img width="1718" height="971" alt="Снимок экрана 2026-03-09 143405" src="https://github.com/user-attachments/assets/d0ccae8f-2f25-40a8-b727-b1f4c2e183d6" />
19. В ответе пришлите ссылку на репозиторий.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
