# Requirements

The scope of this project is to bring together a variety number of data that you generate in a sample db, then create an ui any of you choose to manage the data effectively. 

 - Database should be created in MSSQL Server and the create script must be included in the project files.
 - The backend should be implemented with the project type dotnet core and the sdk .net 5.
 - Front end should be any of a SPA framework or dotnet core mvc or razor pages.

Below are the three entities to be used and we ask you to create crud operations for all of them. 

## Entity Definitions:

### Vehicle Entity:
```
entity Vehicle 
	// Unique vehicle id.
	+ VehicleId (int)

	// Unique plate number for vehicle. Also must be in "#-####-###" format.
	+ PlateNumber (string)

	// Last trip date extracted from the Trip table.
	// Should not be persisted in db. Calculated in real-time with respective data.
	+ LastTripDateTime (datetime, nullable)

	// Total travelled distance for the vehicle.
	// Should not be persisted in db. Calculated in real-time with respective data.
	+ TotalTravelDistanceInKilometers (decimal)

	// Average fuel consumed by the vehicle.
	// Should not be persisted in db. Calculated in real-time with respective data.
	+ AverageFuelConsumptionInLitres (decimal)
}
```

### Trip Entity:
```
entity Trip 
	// Unique vehicle id.
	+ VehicleId (int)
	
	// Unique driver id.
	+ DriverId (int)
	
	// The distance for this trip, in kilometers.
	+ DistanceInKilometers (decimal)
	
	// The fuel consumed for the trip, in litres.
	+ FuelConsumptionInLitres (decimal)
}
```

### Driver Entity:
```
entity Driver 
	// Unique driver id.
	public int DriverId { get; set; }
	
	// The driver's license number.
	public string LicenseNumber {get; set; }
	
	// The total count of the used vehicle distinctly.
	// Should not be persisted in db. Calculated in real-time with respective data.
	public int UsedVehicleCount { get; set; }
}
```

## Implementation

### External library usage
You can use any Nuget library to solve the problem. If you can solve the problem without any Nuget library, it's better.

### Think about big data!
There will be large number of datasets, so aggregation should be as fast as possible. You can alter any entity but you can not change their data types.

### Be careful about null or empty values
Some column values might be null or empty. So please keep in mind while casting them or when using in aggregations.

### Good luck! :)