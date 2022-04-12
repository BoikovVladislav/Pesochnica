pipeline{
  agent any
  environment{
  dockerhub = credentials('Dockerhub_credentials')
  }
  stages{ 
  stage('build image'){
    when{
      branch 'master'
   }
    steps{
    sh 'docker build -t lwhatizlove/apache_repo:server_last_version .'
    }
  }
  stage('pushing to dockerhub'){
     when{
      branch 'master'
   }
    steps{
    sh 'docker tag lwhatizlove/apache_repo lwhatizlove/apache_repo:$GIT_COMMIT'
    sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
    sh 'docker push lwhatizlove/apache_repo:$GIT_COMMIT'
    }
  }
}
}
