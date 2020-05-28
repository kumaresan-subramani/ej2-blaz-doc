#!groovy

node('EJ2Doc') {
    try {
        deleteDir()

        stage('Import') {
            git url: 'https://gitlab.syncfusion.com/essential-studio/ej2-groovy-scripts.git', branch: 'master', credentialsId: env.JENKINS_CREDENTIAL_ID
            shared = load 'src/shared.groovy'
        }

        stage('Checkout') {
            checkout scm
            shared.getProjectDetails()
            shared.gitlabCommitStatus('running')
        }

        stage('Install') {
              shared.install()
        }

        stage('Build') {
            shared.runShell('npm run build')
        }

        // stage('Test') {
        //     shared.test()
        // }

        stage('Publish') {
            shared.publish()
        }

        shared.gitlabCommitStatus('success')
        deleteDir()
    }
    catch(Exception e) {
        shared.throwError(e)
    }
}
