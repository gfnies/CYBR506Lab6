Readme file for Assignment 6 in CYBR 506
1.  Have docker installed and open.
2.  Make sure any containers using ports 1812, 1813 or 5000 are stopped
3.  Open Powershell with admin privileges or equivalent command line interface CLI in other operating systems
4.  Download the files from Github and move them to a working directory
5.  Go to the working directory using the CLI
6.  Go to the freeradius directory   
     cd freeradius
7.  Create the radius image
     docker build -t freeradius-dolphin .
8.  Create and run the radius container
     docker run -d --name freeradius-dolphin-c -p 1812:1812/udp -p 1813:1813/udp freeradius-dolphin
9.  Inspect the ip address in the radius container and compare to the ip address in the app.py file in the flaskapp directory. Use:
     docker inspect freeradius-dolphin-c   
     If they are both 172.17.0.2 no further action is required
	 If docker inspect is 172.17.0.X, edit and save the app.py file to match the ip address obtained with the docker inspect command
10. Create the flaskapp image 
     docker build -t flaskapp-dolphin .
11. Create and run the flaskapp container
     docker run -it -d -p 5000:5000 flaskapp-dolphin
12. Check the docker app and verify both your freeradius-dolphin-c and flaskapp containers are running. Note the flaskapp
     container will have a name of adjective-lastname since we did not specifiy a name.	 If not running start them from the app.
13. Open a browser and type in the address:
     http://127.0.0.1:5000 
14. Type in the username: dolphin   and password: pw123456
15. The result should be: Welcome, dolphin!