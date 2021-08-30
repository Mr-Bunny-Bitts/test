node {
    def server = Artifactory.server 'artifactory-server'
    def uploadSpec = {
  "files": [
        {
             "pattern": "*.zip",
             "target": "AUTOSAR-repo"
        }
        ]
    }
    server.upload(uploadSpec)
}


