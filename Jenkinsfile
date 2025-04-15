pipeline {
  agent {
    docker {
      image 'docker.io/library/php:7.3-fpm-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''curl -f -sS https://getcomposer.org/installer | php \\
    && mv composer.phar /usr/local/bin/composer \\
    && composer self-update --clean-backups \\
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ 
 '''
      }
    }

    stage('Test') {
      steps {
        sh 'composer install && php artisan serve --port 3000'
      }
    }

  }
}