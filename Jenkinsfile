pipeline{
  agent any
  tools{
    maven 'maven-3.6.3'
  }
  stages{
    stage('Maven build'){
      steps{
        sh 'mvn clean package'
      }
    }
    stage('Docker build'){
      steps{
        sh 'docker build -t dedeepya02/docker-jenkins-integration:latest .'
      }
    }
    stage('Docker push'){
      steps{
        withCredentials([usernamePassword(credentialsId: '56a9b4a5-2c17-4853-9214-9be7e473c6ab', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push dedeepya02/docker-jenkins-integration:latest'
      }
    }
  }
}
}
