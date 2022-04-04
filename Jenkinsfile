pipeline {
//    agent { docker { image 'node:16.13.1-alpine' } }
    agent any

    stages {
        stage('echo npm version') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 16 LTS') {
                    sh 'npm --version'
                }
            }
        }
        stage('test') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 16 LTS') {
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }
        stage('build') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 16 LTS') {
                    sh 'npm run build'
                }
            }
        }
        stage('build docker image') {
            steps {
                nodejs(nodeJSInstallationName: 'Node 16 LTS') {
                    sh 'docker push axelvdn/jenkinstest:myjenkins-blueocean:2.332.1-1'
                }
            }
        }
    }
}
