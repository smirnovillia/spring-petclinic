node{
    stage('Build'){
        try{
            stage("SonarQube Quality Gate") {
                        timeout(time: 1, unit: 'HOURS') {
                           def qg = waitForQualityGate()
                           if (qg.status != 'OK') {
                             throw error "Pipeline aborted due to quality gate failure: ${qg.status}"
                           }
                        }
            }
             stage ("Test") {
                     try {
                         sh 'mvn test'
                     } catch(err) {
                         step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
                         throw error
                     }
                 }
         } catch (error) {
             echo "Something goes wrong"
             throw error
         }
     }

     stage ('Deploy') {
         echo "Im deploying now!"
     }
 }
