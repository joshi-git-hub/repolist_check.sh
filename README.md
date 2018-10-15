# repolist_check.sh
#this script is for finding the repolist in any linux machine.
******************@@@@@@@************************************
#!/bin/bash
#########################################################################
##THIS SCRIPT IS FOR FIND THE TOTAL REPOLIST OF ANY UNIX BASED SYSTEMS.#
###############+++++++++++++++++++++++++++++++++++++++#################
if [ $# -eq 1 ]
then
ip=`cat /srv/pass_file |grep $1 |awk '{print$2}'`
pass=`cat /srv/pass_file |grep $1 |awk '{print$3}'`
#sshpass -p $pass ssh -o StrictHostKeyChecking=no root@$ip "yum repolist |grep -i repolist |awk '{print$2}'"
sshpass -p $pass ssh -o StrictHostKeyChecking=no root@$ip "yum repolist |grep -i repolist |awk '{print$2}'" >/var/output/all_repo.txt
cvar="$?"
if [ $cvar -eq 0 ]
then
 echo "*********************total number of repo packages of $1.*********************************"
cat /var/output/all_repo.txt
else
echo "there is somting wrong in either ip or in system."
fi
else
echo "you are doing wroing."
fi
(((((((((((((((((((((((((((((((((((((((((
