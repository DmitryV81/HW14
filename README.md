

127.0.0.1:3000
При первом входе в систему понадобится изменить пароль. По умолчанию логин admin, пароль admin

После смены пароля открывается окно Grafana с приветствием.

Для дальнейшей настройки открываем меню "Configuration" и в нём выбираем пункт "Data sources"

![Data sources step 1](https://github.com/DmitryV81/HW14/blob/main/add_data_sources.png)

Нажимаем кнопку "Add data source". Далее выбираем источник данных Prometheus:

![Data sources step 2](https://github.com/DmitryV81/HW14/blob/main/add_data_source_prometheus.png)

Так как Prometehus и Grafana расположены на одном и том же хосте в поле url указываем http://127.0.0.1:9090 и нажимаем кнопку Save&test

![Data sources step 3](https://github.com/DmitryV81/HW14/blob/main/prometheus_data_source_2.png)

После этого переходим в меню Dashboards -> Import dashboard и указываем ID dashboard 1860. Этот ID взят с сайта https://grafana.com/grafana/dashboards/1860-node-exporter-full/

![Dashboard import](https://github.com/DmitryV81/HW14/blob/main/load_dashboard_node_exporter.png)

Полный список dasboards доступен на сайте https://grafana.com/grafana/dashboards/
 
После введения ID нажимаем кнопку load. Появляется описание dashboard, которое мы хотим загрузить. Внизу в поле prometehus нужно выбрать из выпадающего списка "Prometheus" и нажать кнопку Import 

![Dashboard import step 2](https://github.com/DmitryV81/HW14/blob/main/import_dashboard.png)

В итоге мы получили работающий dashboard от Grafana, на котором отображаются сведения получаемые prometheus от node_exporter расположенного на веб-сервере nginx

![Результат работы](https://github.com/DmitryV81/HW14/blob/main/dashboard_node_exporter.png)

