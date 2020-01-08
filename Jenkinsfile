node{
    stage("SonarQube Quality Gate") {
            timeout(time: 1, unit: 'HOURS') {
               def qg = waitForQualityGate()
               if (qg.status != 'OK') {
                 error "Pipeline aborted due to quality gate failure: ${qg.status}"
               }
            }
        }

    stage ("test") {

        try {
            sh 'mvn test'
        } catch(err) {
            step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
            throw err
        }
    }

    stage ("deploy") {

        echo "Im deploying now!"
    }
}
