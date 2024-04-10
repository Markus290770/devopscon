node {
    def mvnHome
    def GIT_REPO = "https://github.com/nirkoren/devopscon.git"
    def buildCMD = "mvn clean install -Pci"

    stage("Preparation") { 
        println "Cloning git repository..."
        git branch: "main", url: GIT_REPO
        mvnHome = tool 'M3'
    }

    stage('Build & Deploy') {
        println "Starting build..."
        if (isUnix()) {
            sh buildCMD
        } else {
            bat(buildCMD)
        }
        
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
    }
}
