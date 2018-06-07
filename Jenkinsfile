node {
    stage('Checkout code') {
        checkout scm
    }

    stage('Build') {
	version = '1.0.' + env.BUILD_NUMBER
        currentBuild.displayName = version
	sh './mvnw -B -V -U -e versions:set -DnewVersion=$version'
        sh './mvnw -B -V -U -e clean package'
    }

    stage('Archive') {
	sh 'ls -lrt'
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
    }

}
