node {
    stage('Build') {
        sh 'ls -lrt'
        sh './mvnw -B -V -U -e clean package'
    }

    stage('Archive') {
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
    }

}
