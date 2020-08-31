pipeline
{
    agent {
        label 'OneS'
    }
    
    environment {
        envString = 'true'
    }

    post {
        always {
            bat "echo always"
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure']]
            junit allowEmptyResults: true, testResults: 'out/syntax-check/junit/*.xml'
        }
    
        // failure {
        //     bat "echo failure"
        // }
        
        // success {
        //     bat "echo success"      
        // }
    }
    stages {

    stage("Создание тестовой базы") {
            steps {
                bat "chcp 65001\n CALL vrunner init-dev --dt C:/Train_04_20/Template/course.dt --src src/cf --db-user Галкин"
            }
        }

    stage("Синтаксический контроль") {
            steps {
                bat "chcp 65001\n CALL vrunner syntax-check"
            }
        }


        // stage("stage") {
        //     steps {
        //         bat " echo Сообщение из steps"
        //         bat " echo переменная envString = ${envString}"

        //         script {
        //             scannerHome = tool "sonar-scanner"
        //         }

        //     }
        // }
    }
}