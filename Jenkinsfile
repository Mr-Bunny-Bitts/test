node {
    git url: 'https://github.com/Mr-Bunny-Bitts/test.git'
    def server = Artifactory.server 'artifactory-server'
    def uploadSpec = readFile 'test1.json'
    def buildInfo = server.upload spec: uploadSpec
    server.publishBuildInfo buildInfo
}


