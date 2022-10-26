## As prereq, two input binaries need to be download and placed correctly 

1. JDK, roles/linux-jdk/files/jdk-7u80-linux-x64.tar.gz
2. Weblogic server, roles/fmw-software/files/fmw_12.1.3.0.0_wls.jar

Link to download specific version of weblogic 
- JDK: 
    - https://www.oracle.com/java/technologies/javase/javase7-archive-downloads.html
    - IBM internal repo: http://10.134.151.85:8888/java/java7/xLinux64/
- Weblogic: 
    - https://www.oracle.com/middleware/technologies/weblogic-server-installers-downloads.html
    - IBM internal software repo: http://10.134.151.85:8888/oracle/weblogic/v12/base/


## To initiate testing on local vm provisioned by gold image
- Create a VM (Steps are tried in devops lab)
- Run following commands to enable subscription, install binaries, make /tmp executable 
```
sudo subscription-manager repos --enable ansible-2.8-for-rhel-8-x86_64-rpms
sudo subscription-manager register --username **** --password ***** --auto-attach --force
sudo yum install git vim python39 ansible
sudo mount -o remount,exec /tmp
```
- Clone these weblogic-ansible repo
- Download the JDK and weblogic binary to specific path from mentioned links and path above
- Ensure the downloaded file name matches the file name supplied as the input in 'infra-vars.yml'
- Run ansible-playbook weblogic-fmw-domain.yml
