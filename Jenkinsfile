//START-OF-SCRIPT
//comment3
timeout(time: 60, unit: 'SECONDS') {
    node('jenkins-node02') {
        def RELEASENAME = "webapp.war"

        properties([
            pipelineTriggers([pollSCM('H/1 * * * 1-5')])
        ])
        
        def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
        sh "${GRADLE_HOME}/bin/gradle tasks"

        stage('Clone') {
            git url: 'https://github.com/XelK/devops-webapp1.git'
        }

        stage('Build') {
            sh "${GRADLE_HOME}/bin/gradle build -PwarName=${RELEASENAME} --info"
        }

        stage('Archive') {
            //archiveArtifacts "build/libs/${RELEASENAME}"
            archiveArtifacts "build/libs/*.war"
        }    
    }
}
//END-OF-SCRIPT
