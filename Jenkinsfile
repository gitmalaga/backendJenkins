pipeline {
    agent any //para que se ejecute en el nodo principal

    options{

        disableConcurrentBuilds()
        timestamps()
        time : 5
    }

    environment {

        FORCE_COLOR = 0
        NO_COLOR = true
    }


    stages { 
        stage('Audit tools') {
        steps {
            sh 'node --version'
           
              }

             }

        stage('Install dependencies'){
        steps {
            sh 'npm install'
              }

             }

        stage('Format check'){
        steps {
            sh 'npm run format:check'
              }
        
             }

         stage('Code quality'){
         steps {
            sh 'npm run lint'
              }

            }

        stage('Type check'){
         steps {
            sh 'npm type-check'
              }

            }

         stage('Tests'){
         steps {
            sh 'npm run test'
              }

            }

         stage('Build'){
         steps {
            sh 'npm run build'
            sh 'ls -la > server.mjs dist'
            archiveArtifacts(artifacts: 'server.mjs', fingerprint: true)
              }

            }
    }

    post{
        always{
            cleanWs()
        }

        success{
            echo 'Pipeline completed successfully!'
        }

        failure{
            echo 'Pipeline failed. Review logs.'

        }
    }
}