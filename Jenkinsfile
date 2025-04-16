pipeline {
  agent {
    docker {
      image 'php:7.3-fpm-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''sed -i \'s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g\' /etc/apk/repositories
&& apk add curl \\
&& curl -f -sS https://getcomposer.org/installer | php \\
&& mv composer.phar /usr/local/bin/composer \\
&& composer self-update --clean-backups \\
&& composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ 
 '''
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'composer install && php artisan serve --port 3000'
      }
    }

  }
}