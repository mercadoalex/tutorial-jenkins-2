node {
    //groovy syntax
    stage('Check SCM'){
      //Descargamos codigo del repositorio
      echo 'Accediendo al respositorio y descargando el codigo'
      sh 'rm -rf *'
      checkout scm 
    } 
    stage('Build'){
      echo 'Construyendo......'  
      //Configurar variables
      def mvnHome = tool 'M3'  
      env.PATH = "${mvnHome}/bin:${env.PATH}" 
      echo "var mvnHome='${mvnHome}'"
      echo "var env.PATH='${env.PATH}'"
       
    }
    stage('Test'){
        echo 'Probando......'
    } 
    stage('Deploy'){
        echo 'Entregando......'
    } 
}
