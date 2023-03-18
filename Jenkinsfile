pipeline {
  agent{
    label{
      label "built-in"
 customWorkspace "/mnt/pipeline" 
    }
  }
  stages {
    stage ("deploy to container") {
      steps {
        
        sh "sudo docker volume create my-volume"
        sh "sudo cp /mnt/pipeline/index.html /var/lib/docker/volumes/my-volume/_data"
        sh "chmod -R 777 /mnt/pipeline/index.html"
        sh "chmod -R 777 /var/lib/docker/volumes/my-volume/_data"
        sh "sudo docker run -itdp 8085:80 -v my-volume:/usr/local/apache2/htdocs --name container-1 httpd"
  
      }
    }
  }
}
