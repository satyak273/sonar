node("master"){
                stage('Clone Repo') {
                    git branch: 'master',url: 'https://github.com/abdheshkumar/scala-examples'
                }
 
                jdk = tool name: 'jdk-11.0.11', type: 'jdk'
                env.PATH="${env.JAVA_HOME}:${env.PATH}"
 
                stage('Build'){
                    withEnv([
                        "JAVA_HOME=${tool 'jdk-11.0.11'}",
                        "PATH+JAVA=${tool 'jdk-11.0.11'}/bin"
                    ]){
                           bat "sbt -Dsbt.log.noformat=true -DbuildNumber=${BUILD_NUMBER} clean compile"
                       }
                    }
                stage('Code Quality Check via SonarQube') {
                    script {
                       def scannerHome = tool 'SonarQube1';
                           withSonarQubeEnv("SonarQube") {
                           bat "${tool("SonarQube1")}/bin/sonar-scanner \
                           -Dsonar.projectKey=payment_gateway \
                           -Dsonar.java.binaries=. \
                           -Dsonar.sources=. \
                           -Dsonar.css.node=. \
                           -Dsonar.host.url=http://localhost:9000 \
                           -Dsonar.login=637082cfd2d6c7f6e22756b42077047a2a4414a4"
                            }
                        }


               
}
}
