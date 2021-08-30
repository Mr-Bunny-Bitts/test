node {
    git url: 'https://github.com/Mr-Bunny-Bitts/test.git'
    def server = Artifactory.server 'artifactory-server'
    def uploadSpec = readFile 'test-main.zip'
    def buildInfo = server.upload spec: uploadSpec
    server.publishBuildInfo buildInfo
}


