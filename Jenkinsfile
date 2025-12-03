pipeline {
  agent any
  environment {
    MY_GLOBAL_VARIABLE = 'value'
  }
  failure {
    echo «Это будет выполняться, если задача провалилась»
    mail to: «Ваша почта»,
      subject: «${env.JOB_NAME} – Сборка № ${env.BUILD_NUMBER} провалилась»,
        body: «Для получения дополнительной информации о провале пайплайна, проверьте консольный вывод по адресу ${env.BUILD_URL}»
  }
  stages {
    stage('Example') {
      steps {
        echo «Значение моей глобальной переменной: ${env.MY_GLOBAL_VARIABLE}»
      }
    }
  }
  stages {
    stage(«Build») {
      steps {
        echo «Сборка приложения...»
      }
    }
    
    stage(«Test») {
      steps {
        echo «Тестирование приложения...»
      }
    }
    stage(«Deploy») {
      steps {
        echo «Развёртывание приложения...»
      }
    }
  }
  post {
    always {
      deleteDir()
    }
  }
}
