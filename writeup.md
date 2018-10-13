Student describes the effect of the P, I, D component of the PID algorithm in their implementation. Is it what you expected?
The P component stands for Proportional, which allows the controller to add or remove it's correction proportionally to how big the error is. The bigger the error, the bigger the correction, i.e. proportional.
The I component represents the integral of all the previous errors, which is calculated by adding up the sum of all previous errors when using discrete time. This allows the controller to compensate for a bias, such as when the car has a bias in its steering that is making it go slightly to the left the entire time.
The D component reperesents the differential, which is calculated by comparing the difference between two different time samples. So when the difference in CTE is large between two time samples, this component will allow the controller to reduce the CTE quicker.

Student discusses how they chose the final hyperparameters (P, I, D coefficients). This could be have been done through manual tuning, twiddle, SGD, or something else, or a combination!

All in all, the integral part is not really necessary for this project, since we aren't working with something like a gyroscope that requires compensation for a steady bias. I began by using the provided values in Udacity's walkthrough video of -1, 0, -1 for Kp, Ki and Kd respectively. These values did not really do it for the car, but using the positive values 1, 0 and 1 respectively did allow the car to move more reasonably. Due to a lot of oversteering, I decided to limit the maximum steering angle in order to avoid going out of the lanes so much. Also, seeing how I had a problem of "overshooting" from the controller, I decided to up the Kd value, which allowed the car to stay in the lanes somewhat more. These two changes made all the difference, allowing the controller to successfully navigate through the entire course. However, the vehicle was still getting very close to the edges. This was solved by increasing the Kd value, resulting in the final values of:
  Kp = 2
  Ki = 0
  Kd = 20


Now, the car can successfully navigate the entire course without ever getting too close to the edges. which meets the criteria mentioned in the rurbric, also mentioned below for convenience;

"No tire may leave the drivable portion of the track surface. The car may not pop up onto ledges or roll over any surfaces that would otherwise be considered unsafe (if humans were in the vehicle)."

While the car does not pop up onto ledges or roll over any surfaces, I would not want to be in that car since it would make me very car sick...
