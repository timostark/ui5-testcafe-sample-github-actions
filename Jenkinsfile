pipeline {
    tools {nodejs "NodeJs" }
    agent any
    options {
        ansiColor('xterm')
        disableConcurrentBuilds()
    }
    
    stages {
        stage('Run E2E tests') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJs') {
                    sh 'npm install'
                    sh 'npm run e2eJenkins'
                }
            }
            post {
                always {
                          junit keepLongStdio: true,
                          testDataPublishers: [[$class: 'TestCafePublisher']],
                          testResults: '*.xml'
                }
            }
        }
    }
}