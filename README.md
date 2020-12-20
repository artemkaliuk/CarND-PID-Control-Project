# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Description
In this project, lateral and longitudinal controller are implemented. PID controller was taken as a basis for both speed (throttle) and steering control.

The PID controller works as a superposition of three parts: proportional (Kp), integral (Ki) and differential (Kd). The proportional part Kp influences the correction of the control signal by applying an attenuating (or amplifying) coefficient to the control signal, which in our case corresponds to the cross-track error (lateral control) and the speed difference to the set speed (longitudinal control). The integral part Ki is aimed to minimize the systematic offset (e.g., due to misalignment in the steering system or horizontal road inclination). Finally, the differential part Kp should minimize rapid changes in the control signal (e.g., due to sudden bursts of wind).

It is worth noting that the optimal tuning of the lateral controller does not guarantee good results for all speeds. E.g., if the tuning was done at lower speeds, these values for Kp, Ki and Kd might not provide the same system performance at higher speeds. For this project, set speed between 30 and 40 mph was tested. Starting with the PID values mentioned in the lecture (Kp = 0.2, Ki = 0.004, Kd = 3.0), vehicle trajectory stabilization was achieved by tuning the parameters done at 30 mph. At values Kp = 0.1, Ki = 0.01 and Kd = 1.0 for the lateral controller, the system was able to keep the car on track without showing significant oscillating behavior. The Kp component was able to keep the car on track even at sharper turns, the Kd allowed for compensation of the oscilating behavior. At the same time, the longitudinal controller was set to values Kp = 0.1, Ki = 0.001, Kd = 1.0.

It is worth noting, that the system is "doomed" to achieve at least small oscillations as it adapts in a reactive style (by comparing the current vehicle orientation with the ground truth one). Contrary to that, a controller with a lookahead capability would be able to calculate the optimal correction of the control signal for a certain distance in front of the vehicle. This leads to a smoother trajectory.
