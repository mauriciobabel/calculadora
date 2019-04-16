pipeline {
    agent any
        stages {
             stage("CompileJava") {
                steps {
                    sh "./gradlew compileJava"
                }
            }

            stage("UnitTest") {
                steps {
                sh "./gradlew test"
                }
            }

            stage("Build") {
                steps {
                sh "./gradlew build"
                }
            }

            stage("CreateDockerImage") {
                steps {
                sh "sudo docker build -t localhost:5000/calculadora ."
                }
            }

            stage("DockerPush") {
                steps {
                sh "sudo docker push localhost:5000/calculadora"
                }
            }

            stage("DockerStopContainer") {
                steps {
                sh "sudo docker stop calculador || true"
                }
            }

            stage("DockerRemoveContainer") {
                steps {
                sh "sudo docker rm calculador || true"
                }
            }

            stage("RunContainer") {
                steps {
                sh "sudo docker run -d -p 9090:8090 --name calculador localhost:5000/calculadora"
                }
            }
    }
}
