// This Pipeline is for maven projects
pipeline{
    agent any
    tools {
        maven 'Maven 3.5.4'
        jdk 'jdk8'
    }
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
