pipeline {
agent any
stages {
 stage("Code Checkout from GitLab") {
  steps {
   git branch: 'master',
    url: 

'https://github.com/spark-examples/spark-scala-examples.git'
  }
 }
   stage('Code Quality Check via SonarQube') {
   steps {
  

     script {
       def scannerHome = tool 'SonarQube';
           withSonarQubeEnv("SonarQube") {
           bat "${tool

("SonarQube")}/bin/sonar-scanner \
           -Dsonar.projectKey=test1 \
           -Dsonar.java.binaries=. \
           -

Dsonar.sources=. \
           -Dsonar.css.node=. \
           -Dsonar.host.url=http://localhost:9000 \
           -

Dsonar.login=637082cfd2d6c7f6e22756b42077047a2a4414a4"
               }
           }
       }
   }
}
}
