## Про демо
Простое демо которое знакомит с основами работы со стеком elk (elasticsearch, logstash, kibana).
В примере мы сделали конфигурационный файл для парсинга logstash-ем, который обрабатывает датасет с kaggle, в формате csv.

### Настройка окружения:
1. Скачать [logstash](https://www.elastic.co/downloads/logstash) 
2. Скачать [elasticSearch](https://www.elastic.co/downloads/elasticsearch) 
3. Скачать [kibana](https://www.elastic.co/downloads/kibana)
4. Скачать набор данных. В демонстрации был взят 
5. Распаковать датасет по фильмам [Netlfix](https://www.kaggle.com/shivamb/netflix-shows)
6. Перейти в `kibana/config/kibana.yml` и убрать коментарий с строки `elasticsearch.hosts: ["http://localhost:9200"]`
7. Запустить elasticSearch `elastic/bin/elasticsearch.bat` (windows) или `elastic/bin/elasticsearch` (linux) , если запуск был успешен то можно увидеть json ответ при запросе на `localhost:9200`
8. Запустить kibana `kibana/bin/kibana.bat` (windows) или `kibana/bin/kibana` , если запуск был успешен то можно перейти на `localhost:5601`
9. Запустить logstash из командной строки `./logstash/bin/logstash.bat  netflix-logstash.conf` из папки где нахоидтся конфиг и датасет

### Визуалицаия (kibana)
1. Откройте kib
2. Можно также перйти в managment->dev tools и выполнить запрос 
3. Для того чтобы понять попали ли записи датасета можно воспользоваться запросом - `GET /netflix/_count` или тем что указарн по умолчанию (тогда образаем на блок total - value в ответе)
4. Переходим в `stack managment -> index patterns` указываем патерн `netflix` , можно указать что timestamp нам не нужен
5. Далее мы можем перейти в visualize и создать графики или таблицы с имеющимися полями `visualize -> add  -> график`, после их создания сохраняем `save`
6. Переходим в dashboard. Создаём новый dashboard. Добавляем созданые на этапе 5 графики и таблицы
7. Можно смотреть документацию и ролики из неё, чтобы лучше познакомится с основами. Также в dashboard есть готовые примеры.

### Контейнеризация
Есть [пример](https://github.com/JavaUnchained/delivery-automation) по контейнеризации elk стека c использованием FluentD и чтением информации из стандартного выхода docker контейнера. 
По elk в docker есть почти полноценная [документация](https://elk-docker.readthedocs.io). Есть отличный [репозиторий](https://github.com/deviantony/docker-elk) по работе стека в контейнере

### Дополнительные ссылки:
- Документация [logstash](https://www.elastic.co/guide/en/logstash/7.10/index.html)
- Документация [elasticSearch](https://www.elastic.co/guide/index.html)
- Документация [kibana](https://www.elastic.co/guide/en/kibana/7.10/index.html)
- Графана [kibana](https://www.elastic.co/downloads/kibana)
- Более быстрая замена для logstash [FluentD](https://www.fluentd.org)
- [Демо grafana](https://play.grafana.org)
