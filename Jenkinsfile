pipeline {
    agent {
        node {
            label 'maven'
        }
      
    }
environment {
    PATH = "/opt/maven/bin:$PATH"
}

    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }
    stage('SonarQube analysis') {
    environment {
        scannerHome = tool 'ahisri-sonar-server'
    }
    steps {
    withSonarQubeEnv('ahisri-sonarqube-server'){
        sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
    }
}
