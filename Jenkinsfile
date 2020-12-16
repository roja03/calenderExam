pipeline {
    agent any

    environment {
        // The URL of the artifact in Artifactory, that caused the job to be triggered.
        // May be empty if the build isn't triggered by a change in Artifactory.
        RT_TRIGGER_URL = "${currentBuild.getBuildCauses('org.jfrog.hudson.trigger.ArtifactoryCause')[0]?.url}"
    }

    stages {
        stage('Artifactory configuration') {
            steps {
                rtServer(
                        id: "roja-deb-test",
                        url: http://localhost:8081/,
                        credentialsId: CREDENTIALS
                )
            }
        }

        stage('Add build trigger') {
            steps {
                rtBuildTrigger(
                        serverId: "ARTIFACTORY_SERVER",
                        spec: "*/10 * * * *",
                        paths: "generic-libs-local/builds/starship"
                )
            }
        }
    }
}
