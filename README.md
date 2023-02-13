# philosophers_dining

A simulation program that showcases the philosophers' dining problem. It runs until a philosopher dies or every 
single philosopher has eaten a certain amount of times.

## Description of the problem
n philosophers are sitting around a dining table. Between each philosopher lies a fork. The philosophers
must eat to avoid dying. To eat, they must pick up two forks, one in each hand. When a philosopher picks up a fork,
it becomes unavailable to his neighboors. When he is done eating, he puts his forks down, making them available
again. After a philosopher is done eating, he sleeps for a predefined amount of time.

## Process ordering
Each philosopher is a thread. Each fork is a mutex. When a philosopher picks up a fork, the mutex is locked.
When he puts the fork down, the mutex is unlocked. To prevent a philosopher from dying, we need to make sure that
philosophers take turn in eating.

## Threads and mutex problems
There are some issues we need to attend to concerning the threads and mutex.
* data races (threads accessing memory at the same time)
* deadlocks (a thread waiting for a mutex held by another thread and never released)

## Usage
Use make to compile then run with ./philo. The program takes the following arguments :
1) number_of_philosophers 
2) time_to_die (if a philosopher doesn't eat for time_to_die or more, he will die)
3) time_to_eat (the amount of time a philosopher spends eating)
4) time_to_sleep (the amount of time a philosopher spends sleeping)
5) number_of_times_each_philosopher_must_eat (optional)

```bash
make
./philo number_of_philosophers time_to_die time_to_eat time_to_sleep number_of_times_each_philosopher_must_eat
```
## Example
* Philosophers not dying
``` bash
./philo 4 800 200 200 (runs indefinitely)
./philo 2 130 60 60 5 (simulation stops after each philosopher ate 5 times)
```
* Philopher dying
``` bash
./philo 6 100 50 50 (simulation stops after a philosopher died)
```
