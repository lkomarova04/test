pipeline {
  agent any
  environment {
    MY_GLOBAL_VARIABLE = 'value'
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
