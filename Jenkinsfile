node {
    stage('Checkout code') {
        checkout scm
    }

    stage('Build') {
        sh 'ls -lrt'
        sh './mvnw -B -V -U -e clean package'
    }

    stage('Archive') {
	ls -lrt
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
    }

}
