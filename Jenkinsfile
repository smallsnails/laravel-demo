pipeline {
  agent {
    docker {
      image 'mirror.ccs.tencentyun.com/php:7.3-fpm-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Test') {
      steps {
        sh 'php hello.php'
      }
    }

  }
}