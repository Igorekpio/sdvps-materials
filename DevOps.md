Домашнее задание к занятию «Что такое DevOps. СI/СD»
Задание 1
Что нужно сделать:
Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
Установите на машину с jenkins golang.
Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
![image](https://github.com/user-attachments/assets/5227f88b-933f-480e-bf33-22e63d0c1e96)
![image](https://github.com/user-attachments/assets/3918b680-0017-449a-83f5-b360279b4c54)
![image](https://github.com/user-attachments/assets/35ba89b1-fd85-4ce7-92d0-817d73f340c3)


Задание 2
Что нужно сделать:
Создайте новый проект pipeline.
Перепишите сборку из задания 1 на declarative в виде кода.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/Igorekpio/sdvps-materials'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t 172.27.154.103:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'echo "admin" | docker login http://172.27.154.103:8082 -u admin --password-stdin && docker push 172.27.154.103:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}

![image](https://github.com/user-attachments/assets/e81b1ca7-5735-4201-8da0-5d893eae3175)
![image](https://github.com/user-attachments/assets/59080b31-1c86-4773-9471-a2a8438884aa)

Задание 3
Что нужно сделать:
Установите на машину Nexus.
Создайте raw-hosted репозиторий.
Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
Загрузите файл в репозиторий с помощью jenkins.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

![image](https://github.com/user-attachments/assets/1cb4694b-f887-4206-88dc-0c51ee4be418)

pipeline {
    agent any
     environment {
        PATH = "/usr/local/go/bin:${env.PATH}" 
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'go build -o binary /var/lib/jenkins/workspace/pipeline_go_file'
                }
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    sh 'curl -v -u admin:91d23e6b05a94b959018b1fdd9186e70 --upload-file binary http://localhost:8081/repository/my-raw-repo/binary'
                }
            }
        }
    }
}

![image](https://github.com/user-attachments/assets/d305e308-1648-4076-9a84-9a670a630354)



