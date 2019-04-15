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
                sh "docker build -t localhost:5000/calculadora ."
                }
            }

            stage("DockerPush") {
                steps {
                sh "docker push localhost:5000/calculadora"
                }
            }

            stage("RunContainer") {
                steps {
                sh "docker run -d -p 9090:8090 --name calculador localhost:5000/calculadora"
                }
            }
    }
}
