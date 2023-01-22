

127.0.0.1:3000
При первом входе в систему понадобится изменить пароль. По умолчанию логин admin, пароль admin
После смены пароля открывается окно Grafana с приветствием.
Для дальнейшей настройки открываем меню "Configuration" и в нём выбираем пункт "Data sources"

Нажимаем кнопку "Add data source". Далее выбираем источник данных Prometheus:

Так как Prometehus и Grafana расположены на одном и том же хосте в поле url указываем http://127.0.0.1:9090 и нажимаем кнопку Save&test

После этого переходим в меню Dashboards -> Import dashboard и указываем ID dashboard 1860. Этот ID взят с сайта https://grafana.com/grafana/dashboards/1860-node-exporter-full/


Полный список dasboards доступен на сайте https://grafana.com/grafana/dashboards/
 
После введения ID нажимаем кнопку load. Появляется описание dashboard, которое мы хотим загрузить. Внизу в поле prometehus нужно выбрать из выпадающего списка "Prometheus" и нажать кнопку Import 

В итоге мы получили работающий dashboard от Grafana, на котором отображаются сведения получаемые prometheus от node_exporter расположенного на веб-сервере nginx


