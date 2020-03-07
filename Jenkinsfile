
podTemplate(label: 'mypod', serviceAccount: 'jenkins-ci', containers: [ 
    containerTemplate(
      name: 'docker', 
      image: 'docker', 
      command: 'cat', 
      resourceRequestCpu: '50m',
      resourceLimitCpu: '100m',
      resourceRequestMemory: '100Mi',
      resourceLimitMemory: '200Mi',
      ttyEnabled: true
    ),
    containerTemplate(
      name: 'kubectl', 
      image: 'amaceog/kubectl',
      resourceRequestCpu: '50m',
      resourceLimitCpu: '100m',
      resourceRequestMemory: '100Mi',
      resourceLimitMemory: '200Mi', 
      ttyEnabled: true, 
      command: 'cat'
    ),
    containerTemplate(
      name: 'helm', 
      image: 'alpine/helm:2.14.0', 
      resourceRequestCpu: '50m',
      resourceLimitCpu: '100m',
      resourceRequestMemory: '100Mi',
      resourceLimitMemory: '200Mi',
      ttyEnabled: true, 
      command: 'cat'
    )
  ],

  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
    hostPathVolume(mountPath: '/usr/local/bin/helm', hostPath: '/usr/local/bin/helm')
  ]
  ) {
    node('mypod') {
        stage('Get latest version of code') {
          checkout scm
        }
        stage('Check running containers') {
            container('docker') {  
                sh 'hostname'
                sh 'hostname -i' 
                sh 'docker ps'
                sh 'ls'
            }
            container('kubectl') { 
                sh 'kubectl get pods -n default'  
            }
            container('helm') { 
                sh 'helm init --client-only --skip-refresh'
                sh 'helm repo update'
                // sh 'helm history foodapp' 
            }
        }         
    }
}