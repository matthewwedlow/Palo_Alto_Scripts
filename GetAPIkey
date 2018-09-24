import urllib2 
import xml.etree.ElementTree as ET 
import sys
import os
import datetime
import time

ip_address = raw_input('Enter the IP address:   ') or "x.x.x.x" #You can put a default address here
username = raw_input('Enter a username:   ') or "username"
password = raw_input('Enter the password:   ') or "password"
filePath = os.path.join('C:/', 'TestMultiLog' + datetime.datetime.now().strftime("_%m-%d-%y_%S") + '.txt')

str =  "*****Script started*****"

def getTime(): #Gets the current time and formats it
	time = datetime.datetime.now().strftime("%d-%m-%y %H:%M:%S")
	return time

def setLog(str): #Logs to a file and appends newlines
	with open(filePath, 'a') as logFile:
		logFile.write(getTime() + " : " + str + '\n')

def getAPIkey():
	try:
		url = 'https://'+ip_address+'/api/?type=keygen&user='+username+'&password='+password
		response = urllib2.urlopen(url) 
		html = response.read() 
		str = "HTML successfully accessed"
		setLog(str)
	except:
		str = "Invalid credentials or IP address. Check username and password"
		setLog(str)	

	
	contents = ET.fromstring(html)

	if contents.attrib == {'status': 'success'}:
		for item in contents.iter('key'):
			print item.text 
			str = "API Key = " + item.text
			setLog(str)
	else:
		print "API call failed. Check credentials"
		str = "API call failed. Check credentials"
		setLog(str)
		

setLog(str)
getAPIkey()
str = "*****Script complete*****"
setLog(str)
sys.exit(1)
