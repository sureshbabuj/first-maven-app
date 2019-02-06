// This Pipeline is for maven projects
pipeline{
    agent any
    stages{
        stage('clone')
             steps{
              git credentialsId: '1713ee85-d3ae-462b-984f-6b8f15c5a6db', url: 'https://github.com/sureshbabuj/first-maven-app.git'
             }
stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
stage ('send artifacts'){
   steps {
 sshPublisher(publishers: [sshPublisherDesc(configName: 'DevOps52', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ls', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/root/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '/home/suresh/maven/first-maven-app/target')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])

}
    }
}   
}
