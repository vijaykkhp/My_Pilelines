// Globals
def mvnHome = "/opt/apache-maven-3.2.5"
def build_vesion
def sha1
def git_url='https://github.com/WPPg2/avatar-reg.git'
def git_credentialsId='7a9d9c98-fec1-4a3c-82ff-53295d9d5c9b'
def pom_version_tag='avreg_version'

stage 'Build'
   
node('CTF') {
   // Mark the code checkout 'stage'....
   

   // Get some code from a GitHub repository
 
 //  git credentialsId: '7a9d9c98-fec1-4a3c-82ff-53295d9d5c9b' , url: "${git_repo_url}"
 git credentialsId: '7a9d9c98-fec1-4a3c-82ff-53295d9d5c9b', url: 'https://github.com/WPPg2/avatar-reg.git'


   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   //def mvnHome = tool 'M3'


   
   // Run the maven build

   
   //def mvnHome   = tool 'maven-3.2.1'

   build_version = get_version()
   echo "Building version ${build_version}"
   echo "build id is ${env.BUILD_ID}"
   
   
   
   sh "git rev-parse HEAD > sha1"
   
   sha1 = readFile('sha1')
   echo "sha1 is ${sha1}"
  

  // sh "${mvnHome}/bin/mvn clean versions:set -DnewVersion=${build_version}-NIGHTLY-${env.BUILD_ID}"

}


stage 'Create AMI'




node('master') {
   echo "$sha1"
      
}


def get_version() {
  def matcher = readFile('pom.xml') =~ '<avreg.version>(.+)</avreg.version>'
  matcher ? matcher[0][1] : null
}
