pipeline {
  agent {
    docker {
      image 'php:7.3-fpm-alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''curl -f -sS https://getcomposer.org/installer | php \\
    && mv composer.phar /usr/local/bin/composer \\
    && composer self-update --clean-backups \\
    && composer install'''
      }
    }

  }
}