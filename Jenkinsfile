podTemplate(label: 'jenkins-slave-pod',  
  containers: [
    containerTemplate(name: 'docker', image: 'registry.cn-hangzhou.aliyuncs.com/spacexnice/jenkins-slave:latest', command: '', ttyEnabled: false)
  ]
  ,volumes: [
     hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')
  ]) {
    node ('jenkins-slave-pod') {

      stage('Get the jenkins-slave project') {
  
        git url: 'https://github.com/hjue/jenkins-slaves.git'
        
        container('docker') {
          stage('Build blog project') {
    
            sh "docker build -t registry.cn-hangzhou.aliyuncs.com/spacexnice/jenkins-slaves-java8:latest ."
          }
        }
      }

      stage 'Build and push images!'
        container('docker') {
            stage 'build'
      }
}