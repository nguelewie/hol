
pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }

    stages {
        
       stage('build') {
            steps {
                echo 'Hello build'
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'      
            }
        }
       stage ('build and publish image') {
      steps {
        script {
          checkout scm
          docker.withRegistry('', 'http://3.81.15.153:8080/credentials/store/system/domain/_/credential/DockerRegistryID') {
          def customImage = docker.build("nguelewie/hol-pipeline:${env.BUILD_ID}")
          customImage.push()
          }
    }
 
    }
}
    }
}


