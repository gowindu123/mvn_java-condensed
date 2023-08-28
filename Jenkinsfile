pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage("buildjar"){
            steps{
                script{
                    echo "building the application"
                    sh 'mvn package'
                }
            }
        }
        stage("build image"){
            steps{
                script{
                    echo "building the image"
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable:'PASS', usernameVariable: 'USER')]){
                        sh 'docker build -t govindudev/demo-app:jma-4.0 .'
                        sh "echo $PASS | docker login -u $USER --password-stdin"
                        sh 'docker push govindudev/demo-app:jma-4.0'
                    }
                }
            }
        }
        stage('deploy'){
            steps{
                script{
                    
                    echo "deploying the applicationthe application"
                    
                }
            }
        }
    }
}

