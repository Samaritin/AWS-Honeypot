# AWS Honeypot

**Overview:** The goal of this lab was to set up a honeypot in AWS and monitor attack attempts in real time using security tools like Kibana.

**Skills Developed:** Cloud-based honeypot deployment, real-time attack monitoring, AWS configuration.

**Tools Used:** AWS EC2, Kibana, Wireshark, Debian 11.

---

**Lab Details**





AWS honeypot with amazon services

First create an Amazon Web Service account by going into aws.com and signing in with your preferred email then verifying the email or signing in with your aws account if you already have one. It should be noted if the user plans to run this in a vitual machine like virtual box then after creating the account or even starting this honeypot should be done in the virtual machine itself. This will make further steps easier for the individual.  

Once the individual has completed signing in the user will choose a region by selecting the tab in the upright corner next to the users name then the location of their choice. 
Next search for the “EC2” virtual cloud in the search bar at the top. From there the individual will want to launch a new instance. This will be the orange tab on the right hand side. 

Next the user will search for the “Debian 11” under the Debian section of the internet sections. 
For the instance type the user will want a “t2.xlarge”, this will allow the honeypot to seem more realistic and more like a real server and also allow more storage as well. 

Choose new security group and make sure ssh is checked the other two options are optional. Make sure the user saves the security key in a safe place and where the user remembers. This will allow the user to ssh into the Honeypot and see the results and the attacks that are happening. 
Give the honeypot a name. It is also important that the region that the user has chosen will only show the instances that are occurring for that region. For example, if the user chooses a different region this instance will no longer be able to be seen.

Most importantly, the user will choose a key pair name this is how the AWS service will ssh and pair to the service to use the honeypot. In this example, I’m going to be using Linux so I will need to be able to save and find the exact keypair in my linux machine. 
For storage settings next to 1x the user will want to set it to 128. This is a maximum amount, however, this is how the user will save the results from the attacks that the honeypots gets. It is important to note that when an instance is running it will be charging your card for however long it is running even if it is pennies. Therefore, when the user does not want to run this instance running it is best to go back to instances and stop the honeypot.  

Once the instance is created the user can click back to the EC2 dashboard and then instances and it will then appear. Wait for the instance to initialize and give it a few minutes. This may need to refresh and wait for it to say ‘2/2’ then the user can click on the instance and then click on connect at the top. 
Next the user will open the program of their choice to ssh into the honeypot. In this case I will be using Linux on a virtual machine. 
When running the chmod 400 with the key pair. If the user gets a response of no file or directory. Run the command cd Downloads. Then the pwd command. Then list all files by running the ls -l command. Then running the chmod 400 with the keypairname.pem file. 

Next the individual will want to copy the ssh command that is given from the AWS connect screen. Once the admin@ip line appears the honeypot as started. Now the individual is logged into the Amazon machine in the region of choice. From this point on, everything the user will do will be in this terminal with the admin@ip. The honeypot will not load if anything further is run in a normal linux terminal. 

The individual should run a ‘sudo apt update’ then ‘sudo apt-upgrade’ command. This is in essence a new machine and the individual needs to prepare it for the honeypot. To make the honeypot the individual will install the git hub with the ‘sudo apt install git’. Once that is finished clear the screen with ctl L. 
Next the user will download the repository for the honeypot from git hub using the ‘git clone https://github/telekom-security/tpotce.git’ command. Then the user will run ‘ls’ then cd into the directory which will be listed as ‘tpotce’. Then list whats in the directory and the individual will look for an installer shell or install.sh to install the honeypot. The user will run ‘sudo ./install.sh –type=user’ 

In the middle of the installation it will ask yes or no. Click yes. Next it will give you some different options to use. Its best to stick with Standard especially if this is your first honeypot. Next it will ask for the username and password for the honeypot. Once this is done the honeypot will start to install. 
Once this has finished installing the machine will automatically exit. Therefore we need to go back into the AWS service and edit the inbound rules by going to instances, then inbound rules and adding rule custom tcp then selecting my ip for description it’s a choice but the first one is going to be for the ssh, the next rule will be the same but this will be for the web poral. However, the ports will be your choice or you can use the ones I chose which were 64295 and 64297. Then the last one is also custom TCP and the port range is going to be 1 – 64000 and its going to be anywhere IPv4 and this is going to be what the honeypot is on to trap the attacks. Save the rules and remember the ports for the ssh and web portal. 

Now to ssh into the honeypot or the admin@ip the user will run the same command that was given from the AWS service to connect however the user will need to specify the port. In this instance the command is ssh – I “mykey.pem” admin@IP amazonaws.com -p 64295. 

To access the web portal the user will need to go to the instance and click on the instance ID then copy the IPv4 address and put it into the search bar with https:// then the colon with the specified port number. For example, https://38.322.305.333:65397. The user will be hit with a pop up warning of the user of the risk. The user will click advanced and then accept the risk. The user will logon with the same username and password created when downloading the git hub repository. That will log in the user to the dashboard for the honeypot. 

To see the results click on kibana then for the dashboard search >T-Pot and click on the one with live attacks. 


![image](https://github.com/user-attachments/assets/b6d01c1c-7a75-4f15-a562-a0088d7a005c)


![image](https://github.com/user-attachments/assets/4cdae508-b2f0-49eb-ac9b-6e212c5b0e5e)

