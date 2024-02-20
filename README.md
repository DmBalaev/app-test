# Установка и настройка Jenkins для интеграции с тестовым репозиторием
Этот репозиторий содержит инструкции по установке и настройке Jenkins для автоматизации сборки и тестирования вашего проекта.

### Требования
* Jenkins
* Docker
* Ngrok


### 1. Установка ngrok
Ngrok необходим для проброски портов и доступа к Jenkins, установите его, 
следуя инструкции по быстрому старту на [официальном сайте Ngrok.](https://ngrok.com/docs/getting-started/)


### 2. Установка Docker
Установите Docker, следуя инструкциям на [официальном сайте Docker.](https://ngrok.com/docs/getting-started/)

### 3. Установка и настройка Jenkins
1. Скачайте и установите Jenkins, выбрав соответствующий инсталлятор [на официальном сайте Jenkins](https://www.jenkins.io/download/), или воспользуйтесь Docker.
2. Установите необходимые плагины Jenkins, включая "github".
3. После установки, убедитесь, что Jenkins запущен на порту 8080. Затем зайдите в настройки Jenkins и измените 
Jenkins URL на адрес, предоставленный Ngrok (например, `https://84c5df474.ngrok-free.dev`).

### 4.Создание JOB
1. На панели управления Jenkins, нажмите "New Item".
2. Выберите "Pipeline" и введите имя элемента.
3. В разделе Pipeline выберите "Pipeline script from SCM".
4. В разделе SCM выберите "Git" и добавьте URL вашего репозитория (https://github.com/DmBalaev/app-test-with-jenkins.git).
5. Укажите Branch Specifier в настройках вашей ветки (например, */main).
6. Укажите путь к Jenkinsfile в вашем репозитории.
7. Сохраните настройки.

### 4. Добавление Webhook GitHub
1. В настройках вашего GitHub репозитория, перейдите в "Webhooks" и добавьте новый webhook.
2. В поле "Payload URL" введите адрес, предоставленный Ngrok, с добавлением github-webhook/, например, https://84c5df474.ngrok-free.dev/github-webhook/.
3. Выберите "Content type" как application/json.
4. Сохраните настройки.
5. Затем перейдите в настройки вашего проекта в Jenkins и добавьте триггер "GitHub hook trigger for GITScm polling" в разделе Build Triggers.

### Завершение
Теперь ваш проект готов к автоматизации с помощью Jenkins. При каждом обновлении вашего репозитория Jenkins будет автоматически собирать проект.

Чтобы настроить CI/CD для своего репозитория, выполните эти шаги, учитывая, что ваш репозиторий должен содержать файл Jenkinsfile с необходимыми скриптами. 
Дополнительную информацию о Pipeline Jenkins можно найти в [документации по Jenkins Pipeline.](https://www.jenkins.io/doc/book/pipeline/)