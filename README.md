Docker Image Repo Template                                                      
==========================                                                      
                                                                                
This repository is meant to serve as a template for application developers who  
would like to utilize the Image building pipeline in Jenkins. This pipeline     
has a number of expectations of the repository that are listed below.            
                                                                                
Dockerfile                                                                      
----------                                                                      
                                                                                
The Dockerfile must contain the following three comments:                       
                                                                                
.. code:: bash                                                                  
                                                                                
  # APP_NAME = app_name                                                         
  # APP_VERSION = v1.0                                                          
  # APP_REVISION = 1.0                                                          
                                                                                
The APP_NAME will eventually map to the private registry/repo in AWS while the  
APP_VERSION and APP_REVSION will be concatenated to generate the current tag     
for the image. The APP_VERSION is meant to represent the actual version of      
the application while the APP_REVISION is supposed to indicate the current      
revision of this particular version.                                             
                                                                                
tests/                                                                          
------                                                                          
                                                                                
This folder will hold the test scripts that verify this image behaves as        
expected. The Jenkins pipeline will expect a main.sh script in this             
folder that it can execute against a server that has deployed this image locally 
using `docker run`. In order to pass the Test stage of the pipeline this        
script needs to return with a 0 exit status and a non-zero status otherwise.    
Upon a non zero exist status, Jenkins will pass back the STD_ERR to to the      
Jenkins administrators.                                                         
                                                                                
run_opts                                                                        
--------                                                                        
                                                                                
In case the developer would like to add any extra options to the `docker run`   
command (for example, exposing certain ports), these can be added in a file     
at the top level of the repository containing the extra options (eg:          
- p 18080:8080)  

CHANGELOG
---------
This file should contain change log entries in relation to each revision.

