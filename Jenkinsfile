node {
    // The URL of the artifact in Artifactory, that caused the job to be triggered.
    // May be empty if the build isn't triggered by a change in Artifactory.
    def rtTriggerUrl = currentBuild.getBuildCauses('org.jfrog.hudson.trigger.ArtifactoryCause')[0]?.url

    def server = Artifactory.newServer url: http://localhost:8081/artifactory, credentialsId: CREDENTIALS

    stage('Trigger build') {
        server.setBuildTrigger spec: "*/10 * * * *", paths: "generic-libs-local/builds/starship"
    }
}
