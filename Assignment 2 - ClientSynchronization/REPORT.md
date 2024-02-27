# Observations
After running the code the first time the output didn't return what we expected.
The output was the following:
```
Hi,Andreas : 10 : Seats available for Troll
Hi,Xiangming : 10 : Seats available for Troll
Hi,Sam : 10 : Seats available for Troll
Hi,Ilaria : 10 : Seats available for Troll
Congratulations, Andreas : Booked 4 seats for Troll
Congratulations, Xiangming : Booked 3 seats for Troll
Congratulations, Sam : Booked 3 seats for Troll
Sorry, Ilaria : No seats available for Troll
```
The problem is that it doesn't print out the correct amount of seats available for the movie. The problem is that
each thread executes simultaneously and the server doesn't have time to update the amount of seats available before 
the next thread executes. To fix this we need to synchronize the server so that only one thread can execute at a time.
By making the bookTicket method synchronized we can make sure that only one thread can execute at a time. 
``` 
public synchronized void bookTicket(String customerName, int numberOfSeats)
```

Now when the bookTicket() is run, it prevents multiple threads from booking seats simultaneously. The drawback
of using synchronization is that it slows down the program, since each thread has to wait for one another to finish.