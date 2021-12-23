# Управление заданиями MapReduce

## Создать задание {#create}

{% list tabs %}

* Консоль управления

    1. Перейдите на страницу каталога и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера и выберите вкладку **Задания**.
    1. Нажмите кнопку **Создать задание**.
    1. (Опционально) Укажите имя задания.
    1. В поле **Тип задания** выберите `Mapreduce`.
    1. Выберите один из типов драйвера и укажите, что использовать для запуска задания:
        * имя основного класса;
        * путь к основному JAR-файлу в формате:

           {% include [Допустимые пути к файлам](../../_includes/data-proc/jar-file-path-requirements.md) %}

    1. Укажите аргументы задания.

       {% include [Особенности указания аргументов, свойств и настроек](../../_includes/data-proc/job-properties-requirements.md) %}

    1. (Опционально) Укажите пути к дополнительным JAR-файлам, если они используются.
    1. (Опционально) Задайте дополнительные настройки:
        * Укажите пути к необходимым файлам и архивам.
        * Укажите свойства задания.
    1. Нажмите кнопку **Создать задание**.

* CLI

    {% include [cli-install](../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../_includes/default-catalogue.md) %}

    Чтобы создать задание:

    1. Посмотрите описание команды CLI для создания заданий типа `Mapreduce`:

        ```bash
        yc dataproc job create-mapreduce --help
        ```

    1. Создайте задание (в примере приведены не все доступные параметры):

        ```bash
        yc dataproc job create-mapreduce \
           --cluster-name <имя кластера> \
           --name <имя задания> \
           --main-class <имя основного класса> \
           --file-uris <путь к файлу> \
           --archive-uris <пути к архивам> \
           --properties <свойство задания> \
           --args <аргумент> \
        ```

        Пути к необходимым для выполнения задания файлам передавайте в формате:

        {% include [Допустимые пути к файлам](../../_includes/data-proc/jar-file-path-requirements.md) %}

    Идентификатор и имя кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

* API

    Воспользуйтесь методом API [create](../api-ref/Job/create) и передайте в запросе:

    * идентификатор кластера в параметре `clusterId`;
    * имя задания в параметре `name`;
    * свойства задания в параметре `mapreduceJob`.

    Идентификатор кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

{% endlist %}

## Получить список заданий {#list}

{% list tabs %}

* Консоль управления

    1. Перейдите на страницу каталога и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера и выберите вкладку **Задания**.

* CLI

    {% include [cli-install](../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../_includes/default-catalogue.md) %}

    Чтобы получить список заданий, выполните команду:

    ```bash
    yc dataproc job list --cluster-name <имя кластера>
    ```

    Идентификатор и имя кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

* API

    Воспользуйтесь методом API [list](../api-ref/Job/list) и передайте идентификатор кластера в параметре `clusterId` запроса.

    Идентификатор кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

{% endlist %}


## Получить общую информацию о задании {#get-info}

{% list tabs %}

* Консоль управления

    1. Перейдите на страницу каталога и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера и выберите вкладку **Задания**.
    1. Нажмите на имя нужного задания.

* CLI

    {% include [cli-install](../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../_includes/default-catalogue.md) %}

    Для получения общей информации о задании выполните команду:

    ```bash
    yc dataproc job get \
       --cluster-name <имя кластера> \
       --name <имя задания>
    ```

    Идентификатор и имя кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

* API

    Воспользуйтесь методом API [get](../api-ref/Job/get) и передайте в запросе:

    * Идентификатор кластера в параметре `clusterId`. Его можно получить со [списком кластеров в каталоге](./cluster-list.md#list).
    * Идентификатор задания в параметре `jobId`. Его можно получить со [списком заданий в кластере](#list).

{% endlist %}


## Получить логи выполнения задания {#get-logs}

{% include [get-logs-info](../../_includes/data-proc/note-info-get-logs.md) %}

{% list tabs %}

* Консоль управления

    1. Перейдите на страницу каталога и выберите сервис **{{ dataproc-name }}**.
    1. Нажмите на имя нужного кластера и выберите вкладку **Задания**.
    1. Нажмите на имя нужного задания.

* CLI

    {% include [cli-install](../../_includes/cli-install.md) %}

    {% include [default-catalogue](../../_includes/default-catalogue.md) %}

    Чтобы получить логи выполнения задания, выполните команду:

    ```bash
    yc dataproc job log \
       --cluster-name <имя кластера> \
       --name <имя задания>
    ```

    Идентификатор и имя кластера можно получить со [списком кластеров в каталоге](./cluster-list.md#list).

* API

    Воспользуйтесь методом API [listLog](../api-ref/Job/listLog) и передайте в запросе:

    * Идентификатор кластера в параметре `clusterId`. Его можно получить со [списком кластеров в каталоге](./cluster-list.md#list).
    * Идентификатор задания в параметре `jobId`. Его можно получить со [списком заданий в кластере](#list).

{% endlist %}