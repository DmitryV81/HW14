Домашняя работа по теме "Настройка мониторинга

Задание:

Настроить дашборд с 4-мя графиками

    память;
    
    процессор;
    
    диск;
    
    сеть.
    
    Настроить на одной из систем:
    
    zabbix (использовать screen (комплексный экран);
    
    prometheus - grafana.

    использование систем, примеры которых не рассматривались на занятии.
    
    Список возможных систем был приведен в презентации.
    
    В качестве результата прислать скриншот экрана - дашборд должен содержать в названии имя приславшего.

Ход выполнения домашнего задания.

Для автоматизации развертывания системы я использую ansible и vagrant

В Vagrantfile описано создание двух виртуальных машин webserver и prometheus

На ВМ webserver устанавливаем nginx и node_exporter для сбора метрик

На ВМ prometheus устанавливаем prometheus и grafana для графического отображения метрик

Для запуска системы используем команду

```
vagrant up
```
Далее происходит установка и настройка необходимых компонентов через ansible

После завершения установки ВМ webserver доступна по адресу 127.0.0.1:8080, ВМ в части Grafana: 127.0.0.1:3000, ВМ в части Prometheus: 127.0.0.1:9090

В веб-баузере переходим на страницу:

http://127.0.0.1:3000

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

