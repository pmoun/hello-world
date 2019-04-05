pipeline {
    agent { label 'gcp' }
 tools{
  maven 'm3'
 }
    stages {
        stage('build') {
            steps {
                echo 'Clean Build'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh 'mvn test'
            }
        }
        stage('JaCoCo') {
            steps {
                echo 'Code Coverage'
                jacoco()
            }
        }
        stage('Sonar') {
            steps {
                echo 'Sonar Scanner'
          withSonarQubeEnv('sonar') {
                sh 'mvn clean install  -D sonar.host.http://54.165.11.192:9000/sonar'
          }
          }
        }
        stage('Package') {
            steps {
                echo 'Packaging'
                sh 'mvn package'
            }
        
    
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                sh 'mvn deploy'
            }
        }
    }
    
}
