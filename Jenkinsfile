pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '2123cf58-3801-48c0-b927-2c5e3e489608', path: '', url: 'http://localhost:8080')], contextPath: '/mohamed', war: '**/*.war' }
 }
 }
 }
}
