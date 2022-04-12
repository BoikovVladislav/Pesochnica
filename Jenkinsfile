pipeline{
  agent any
  tools{
    maven 'maven'
    jdk 'java'
  }
  environment{
  dockerhub = credentials(Dockerhub_credentials)
  }
  
  stage('build_image'){
    when{
      branch 'master'
   }
    step{
    sh 'docker build -t lwhatizlove/apache_repo:server_last_version .'
    }
  }
  stage('pushing to dockerhub'){
    sh 'docker tag lwhatizlove/apache_repo lwhatizlove/apache_repo:$GIT_COMMIT'
    sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
    sh 'docker push lwhatizlove/apache_repo:$GIT_COMMIT'
  }
}
