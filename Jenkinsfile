pipeline {
    agent any //para que se ejecute en el nodo principal

    stages { 
        stage('Etapa inicial') {
        steps {

            sh 'ls -alh' //para ver dntro de jnkins los fichros a los qu tengo acceso
            sh 'node --version'
            sh 'npm --version'
              }

             }

        stage('Etapa instalación dependencias'){
        steps {
            sh 'npm install'
              }

             }

        stage('Etapa Check buenas prácticas'){
        steps {
            sh 'npm run format:check'
              }
        
             }

         stage('Etapa cheque ficheros'){
         steps {
            sh 'npm run lint'
              }

            }


         stage('Etapa hacer tests'){
         steps {
            sh 'npm run test'
              }

            }



    }

    post{
        always{
            clearWS()
        }

        success{
            echo 'Pipeline ejecutada con éxito'
        }

        unstable{
            echo 'Pipeline ejecutada con errores'
        }

        failure{
            echo 'Pipeline fallida. Revisa los logs'

        }
    }
}