pipeline {
    agent { any }
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
                sh 'mvn clean sonar.host.http://3.86.86.45:9000'
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
