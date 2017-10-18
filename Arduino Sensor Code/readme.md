#Create a string of data.....Following the scheme.
#Example python reading and writing into mongo DB 

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
    
