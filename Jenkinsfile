node(label: 'master') {
    //Variables
    def gitURL='https://github.com/narendrajava1/easy-notes.git'
    def repoBranch='master'
    
    stage('Git-Checkout'){
        gitClone "${gitURL}","${repoBranch}"
        
    }
}

def gitClone(def url,def branch){
    checkout([$class: 'GitSCM', branches: [[name: '${branch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: '${url}']]])
}
