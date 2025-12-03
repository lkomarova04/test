pipeline {
    agent any

    environment {
        MY_GLOBAL_VARIABLE = 'value'
    }

    stages {

        stage('Example') {
            steps {
                echo "Значение моей глобальной переменной: ${env.MY_GLOBAL_VARIABLE}"
            }
        }

        stage('Build') {
            steps {
                echo "Сборка приложения..."
            }
        }

        stage('Test') {
            steps {
                echo "Тестирование приложения..."
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Развёртывание приложения на STAGING..."
                sh "./deploy staging"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Развёртывание приложения на PRODUCTION..."
                sh "./deploy production"
            }
        }
    }

    post {

        failure {
            echo "Это будет выполняться, если задача провалилась"

            mail(
                to: 'Ваша почта',
                subject: "${env.JOB_NAME} – Сборка № ${env.BUILD_NUMBER} провалилась",
                body: "Для получения дополнительной информации проверьте консольный вывод: ${env.BUILD_URL}"
            )
        }

        always {
            deleteDir()
        }
    }
}
