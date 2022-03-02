Authour: Joseph Cates

contact: jcates5@uoregon.edu

project description: calculator to find opening and closing time for brevets. brevets are long distance cycling event, with checkpoints that have opening time, the earliest you can continue on to the next checkpoint and closing times, the lastest you reach the checkpoint and continue on in the event. Each distance bracket (0km - 200km, 201km - 400km, 401km-600km, 601km-1000km) have maximum and minimum speeds, that are used to find the opening and closing time for each checkpoint. For example if an event has a checkpoint at 200km, then the final checkpoint will have a opening time of 20km/34km per hour, where 34 is the maximum speed for the first 200 km. If the next checkpoint is at 400km, then the opening time would be 200km (the distance you can travel at the speed set in the 201km-400km bracket) / 32, (where 32 is the maximum speed for the next 200km) + 200/34, the time it takes to open the first checkpoint. My algorithm takes the given checkpoint distance and goes into the corresponding distance interval. It then subtracts the total brevet distance from the checkpoint, then subtracts 200 (or 400 for 1000) - the previous value to find how much distance was traveled in that speed interval. It then calculates the time for that distance and speed described above, adds the time it takes do that distance to the total time. It then subtracts that distance from the given checkpoint, so the cycle can continue until the control points is at zero. At which point the total time is rounded and then returned. Added a mongoDB database to this project, so you can now save all your inputted data by pressing submit. This clears all the fields and allows you to put in new values to test, without losing the previous values. As if you press Display, all the values that were present on the page when submit was pressed are put back on the page.

Added a flask rest API to the project that communicates with the database to make the overall implementation much cleaner.  The API commands are as follows:

  GET http://API:PORT/api/brevets  displays all brevets stored in the database.

  GET http://API:PORT/api/brevet/ID  displays brevet with id ID.

  POST http://API:PORT/api/brevets  inserts brevet object in request into the database.

  DELETE http://API:PORT/api/brevet/  deletes brevet with id ID.

  PUT http://API:PORT/api/brevet/ID  updates brevet with id ID with object in request.
  



To run this project download the repository, docker and docker compose, create a .env file based off the given template, and then run docker
