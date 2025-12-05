pipeline {
    agent any
    environment{
        SCANNER_HOME = tool 'sonar-scanner'
    }    
    tools{
        maven 'maven3'
        jdk 'jdk11'
    }    

    stages {
        stage('git Checkout') {
            steps {
               git branch: 'main', changelog: false, credentialsId: 'github-creds', poll: false, url: 'https://github.com/ahmed-sayed-devops/simple-jenkins-project.git'
            }
        }
        stage('COMPILE'){
            steps{
                sh 'mvn clean compile -Dskiptest=true'
            }
        }  
        stage('OWASP Dependency Check') {
            steps {
               dependencyCheck odcInstallation: 'DP',
                        additionalArguments: '''
                            --project "ecart-app"
                            --scan .
                            --format HTML
                            --out .
                        '''

              publishHTML([
               allowMissing: false,
               alwaysLinkToLastBuild: true,
               keepAll: true,
               reportDir: '',
               reportFiles: 'dependency-check-report.html',
               reportName: 'OWASP Dependency Check Report'
            ])
        }
      }
        stage('sonarQube Scan'){
            steps{
                withSonarQubeEnv('sonar-server'){
                    sh '''
                     $SCANNER_HOME/bin/sonar-scanner \
                     -Dsonar.projectName=Shopping-Cart \
                     -Dsonar.java.binaries=. \
                     -Dsonar.projectKey=Shopping-Cart 
                    '''
                }
            }
        } 
        stage('BUILD'){
            steps{
                sh 'mvn clean package -Dskiptest=true'
            }
        } 
        stage('Docker Build & Push'){
            steps{
               withDockerRegistry(credentialsId: 'dockerhub-creds', url: 'https://index.docker.io/v1/') {
                 sh "docker build -t shopping-cart -f docker/Dockerfile ."
                 sh "docker tag shopping-cart a7medsayed/shopping-cart:latest"
                 sh "docker push a7medsayed/shopping-cart:latest"
              }
            }
        }   
        stage('Deploy'){
            steps{
                script{
                  withDockerRegistry(credentialsId: 'dockerhub-creds', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker run -d --name merch-shop \
                        --ulimit nofile=65535:65535 \
                        -p 8070:8070 \
                        -e JAVA_OPTS="-Xms128m -Xmx512m -Djava.security.egd=file:/dev/./urandom -Djava.io.tmpdir=/tmp" \
                        a7medsayed/shopping-cart:latest
                    '''
                  }
              }
            }
        }         
    }
}
