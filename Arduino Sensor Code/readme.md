#Create a string of data.....Following the scheme.
#Example python reading and writing into mongo DB 

#!/usr/bin/env python
import pymongo
from pymongo import MongoClient
from datetime import datetime
import serial

client = MongoClient()

db = client.brap_database
sessionsdata = db.sessionsdata

ser = serial.Serial(
	port='/dev/ttyACM1',
	baudrate=115200,
)


#with open(outfile, 'a') as f:   #appends the file
	while ser.isOpen():
		datastring = sio.readline()
		parsed_data = datastring.split("'")
		datarow = {
			"time" : datetime.datetime.utcnow(),
			"data" : {
				"tempf"  : parsed_data[0], 
				"tempr"  : parsed_data[1],
				"fronts" : parsed_data[2],
				"rears"  : parsed_data[3],
				"ax"     : parsed_data[4],
				"ay"	 : parsed_data[5],
				"az"	 : parsed_data[6],
				"gx"	 : parsed_data[7],
				"gy"	 : parsed_data[8],
				"gz"	 : parsed_data[9],

			}
		}

		datarow_id = sessionsdata.insert_one(datarow).inserted_id
		

		#\t is tab; \n is line separator
		#f.write(datetime.utcnow().isoformat() + '\t' + datastring + '\n')
		#f.flush()  #forcing the sytstem to write to the disk

ser.close()		
