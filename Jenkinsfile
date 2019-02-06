// This Pipeline is for maven projects
pipeline{
    agent any
    stages{
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
                sh '/usr/local/src/apache-maven/bin/mvn install' 
            }
        }
stage ('send artifacts'){
   steps {
sshPublisher(publishers: [sshPublisherDesc(configName: 'DevOps52', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ls', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/root/', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '$WORKSPACE/*.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])

}
    }
}   
}
