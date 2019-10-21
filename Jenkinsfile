node('master'){
   stage('git checkout'){
                  git 'https://github.com/Palanimks/parking_backend.git'
              }
   stage ('code analysis')
            sh 'sonar:sonar -Dsonar.login=admin -Dsonar.password=admin'
   
   stage('java build'){
             sh 'mvn clean install sonar:sonar -Dsonar.password=admin -Dsonar.login=admin'
         }
   stage('Deploy')
             sh 'mvn clean Deploy'
   
   
   stage('Running java backend application'){
             sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=dev -jar $WORKSPACE/target/*.jar &'
         }
}
