@Library('easy-notes') _
node(label: 'master') {
    //Variables
    def gitURL='https://github.com/narendrajava1/easy-notes.git'
    def repoBranch='master'
    
    stage('Git-Checkout'){
        gitClone "${gitURL}","${repoBranch}"
        
    }
}


