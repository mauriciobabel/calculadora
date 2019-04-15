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
    }
}
