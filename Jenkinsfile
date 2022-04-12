pipeline{
  agent any
  environment{
  dockerhub = credentials('Dockerhub_credentials')
  }
  stages{ 
  stage('build image'){
    steps{
    sh 'docker build -t lwhatizlove/apache_repo:$GIT_COMMIT .'
    }
  }
  stage('pushing to dockerhub'){
    steps{
    sh 'docker tag lwhatizlove/apache_repo lwhatizlove/apache_repo:$GIT_COMMIT'
    sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
    sh 'docker push lwhatizlove/apache_repo:$GIT_COMMIT'
    }
  }
}
}
