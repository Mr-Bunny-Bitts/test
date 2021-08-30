node {
    def server
    def buildInfo
    def rtMaven
    
    stage ('Clone') {
        git url: 'https://github.com/Mr-Bunny-Bitts/test.git'
    }
 
    stage ('Artifactory configuration') {
        // Obtain an Artifactory server instance, defined in Jenkins --> Manage Jenkins --> Configure System:
        server = Artifactory.server('artifactory-server')

        rtMaven = Artifactory.newMavenBuild()
        rtMaven.tool = "M3" // Tool name from Jenkins configuration
        rtMaven.deployer releaseRepo: 'jenkins_maven-libs-release', snapshotRepo: 'jenkins_maven-libs-snapshot', server: server
        rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        rtMaven.deployer.deployArtifacts = true // Disable artifacts deployment during Maven run
        buildInfo.env.capture = true
        buildInfo = Artifactory.newBuildInfo()
    }
 
    stage ('Deploy') {
        rtMaven.deployer.deployArtifacts buildInfo
    }
        
    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}


