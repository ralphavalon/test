node {
    checkout scm

    stage('Build & Test') {
	    version = '1.0.' + env.BUILD_NUMBER
        currentBuild.displayName = version
	    sh "./mvnw -B -V -U -e versions:set -DnewVersion=$version"
        sh './mvnw -B -V -U -e clean package'
    }

    stage('Archive') {
        junit allowEmptyResults: true, testResults: '**/target/**/TEST*.xml'
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
    }

    stage('Deploy') {
        sh 'ls -lrth'
        if (currentBuild.result == null || currentBuild.result == 'SUCCESS') { 
            if (env.BRANCH_NAME == 'master') {
                echo 'Deploy PROD - I only execute on the master branch'
            } else {
                echo 'Deploy Staging - I execute elsewhere'
            }
        }
    }

}
