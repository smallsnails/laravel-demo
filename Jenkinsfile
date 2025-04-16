pipeline {
  agent {
    docker {
      image 'php:7.3-fpm-alpine'
      args '-u root -p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh "sed -i \'s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g\' /etc/apk/repositories"
        sh "apk add curl"
        sh "curl -f -sS https://getcomposer.org/installer | php"
        sh "mv composer.phar /usr/local/bin/composer"
        sh "composer self-update --clean-backups"
        sh "composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/"
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      when {
        branch "test"
      }
      steps {
        sh "composer update"
        sh "php artisan serve --port 3000"
      }
    }

  }
}
