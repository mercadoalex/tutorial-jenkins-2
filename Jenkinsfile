node {
    //groovy syntax
    stage 'Check SCM' 
    //Descargamos codigo del repositorio
    echo 'Accediendo al respositorio y descargando el codigo'
    //sh 'rm -rf *'
    checkout scm 
    
    stage 'Build'
    echo 'Construyendo......'  
    //Configurar variables
    def mvnHome = tool 'M3'  
    env.PATH = "${mvnHome}/bin:${env.PATH}" 
    echo "var mvnHome='${mvnHome}'"
    echo "var env.PATH='${env.PATH}'"

    // --Compilando
    echo 'Compilando aplicacion'
    sh 'mvn clean compile'    
       
    //Etapa de pruebas
    stage 'Test'
    echo 'Ejecutando pruebas......'
    try{
         sh 'mvn verify'
         step([$class: 'JUnitResultArchiver',testResults: '**/target/surefire/-reports/TEST-*.xml'])    
    } catch(err){
         step([$class: 'JUnitResultArchiver',testResults: '**/target/surefire/-reports/TEST-*.xml'])    
         if (currentBuild.result = 'UNSTABLE')
             currentBuild.result = 'FAILURE'
         throw err    
    }

    stage 'Deploy'
    echo 'Entregando......'

}
