# Multi-Objective Optimization of Suspension Kinematics

This page presents extra material obtained in the case study presented on conference paper 238 - Multi-Objective 
Optimization of Suspension Kinematics of a Race Car, published* in [IAVSD 2021](https://iavsd2021.ru/).

(*) Full paper submitted, publication confirmation pending.

Authors:
- [Ariel Avi](https://www.linkedin.com/in/aviariel/)
- [Claude Rouelle](https://www.linkedin.com/in/claude-rouelle-1810409/)
- [Andrea Piga Carboni](https://www.linkedin.com/in/andrea-piga-carboni-032706180/)

## Overview

The optimization was run on a AWS c5a.8xlarge Ubuntu instance, running on 32 parallel threads. The total time needed 
to run the 4000 generations was approximately 9 hours and 42 minutes. The genetic algorithm settings were:
- Maximum generations: 4000
- Population size: 300
- Mutation rate: 5%
- Mutation method: Gaussian mutation, 2mm standard deviation
- Crossover method: Voluminal BLX-alpha, alpha=2$
- Selection for reproduction: Ranked, 1 rank per generation
- Selection for replacement: Truncation, 150 individuals per generation

## Baseline Suspension

The baseline system uses a Double A-Arm suspension on the front axle and a Five Links on the rear axle.

![](images/baseline-front.png)
Fig. 1 - Baseline Suspension: Front View

![](images/baseline-iso.png)
Fig. 2 - Baseline Suspension: Isometric View

![](images/baseline-side.png)
Fig. 3 - Baseline Suspension: Side View

![](images/baseline-top.png)
Fig. 4 - Baseline Suspension: Top View

![](images/baseline-front_axle-front.png)
Fig. 5 - Baseline Suspension: Front axle on front view

![](images/baseline-rear_axle-front.png)
Fig. 6 - Baseline Suspension: Rear axle on front view

## Optimization

### Boundaries

The boundaries for this case study were chosen arbitrarily, based on experience and were set to large values in order 
to prove that the optimization algorithm can still cope with big search spaces. More details are presented on the paper
itself.

Spherical shapes were used as the outboard boundaries while box shapes were used in the inner boundaries. Each color
represents a different suspension link - or body. The system shown in the boundaries images is the baseline
configuration.

![fig7](images/boundaries-front.png)
Fig. 7 - Boundaries - Front View

![fig8](images/boundaries-rear.png)
Fig. 8 - Boundaries - Rear View

![fig9](images/boundaries-iso.png)
Fig. 9 - Boundaries - Isometric View

![fig10](images/boundaries-side.png)
Fig. 10 - Boundaries - Side View

![fig11](images/boundaries-top.png)
Fig. 11 - Boundaries - Top View

### Objective functions

The objective functions are divided between several evaluation motions. An evaluation motion is the motion that 
defines how the the individual should be evaluated (heave, roll, pitch, steering, or a combination of them). The
objectives are shown preceeded by their respective evaluation motions, following the pattern \<Motion\> : 
\<Objective\>.

The evaluations were given in the form:
- Heave: from -30mm to +30mm displacement w.r.t. the static position.
- Roll: from -3deg to +3deg, with the axis of rotation set fixed, given by the line that connects the points
A(1, 0, 0) and B(-1, 0, 0).
- Pitch: from -1deg to +1deg, with the axis of rotation set fixed, given by the line that connects the points
A(0, 1, 0) and B(0, -1, 0).
- Steering: from -270deg to +270deg at the steering wheel with a rack ratio (mm/revolution) of 60.40.

![fig12](images/heave.front.half_track_l.png)
Fig. 12 - Heave: Half Track (Front Left)

![fig13](images/heave.rear.half_track_l.png)
Fig. 13 - Heave: Half Track (Rear Left)

![fig14](images/heave.front.toe_angle_l.png)
Fig. 14 - Heave: Toe Angle (Front Left)

![fig15](images/heave.rear.toe_angle_l.png)
Fig. 15 - Heave: Toe Angle (Rear Left)

![fig16](images/heave.front.roll_center_gnd.z.png)
Fig. 16 - Heave: Roll Center Z (Front)

![fig17](images/heave.rear.roll_center_gnd.z.png)
Fig. 17 - Heave: Roll Center Z (Rear)

![fig18](images/heave.front.mechanical_trail_l.png)
Fig. 18 - Heave: Mechanical Trail (Front Left)

![fig19](images/heave.front.scrub_radius_l.png)
Fig. 19 - Heave: Scrub Radius (Front Left)

![fig20](images/roll.front.camber_angle_l.png)
Fig. 20 - Roll: Camber Angle (Front Left)

![fig21](images/roll.rear.camber_angle_l.png)
Fig. 21 - Roll: Camber Angle (Rear Left)

![fig22](images/roll.front.roll_center_gnd.y.png)
Fig. 22 - Roll: Roll Center Y (Front)

![fig23](images/roll.rear.roll_center_gnd.y.png)
Fig. 23 - Roll: Roll Center Y (Rear)

![fig24](images/pitch.anti_dive_percent_l_front.png)
Fig. 24 - Pitch: Anti-Dive Percentage

![fig25](images/pitch.anti_squat_percent_l_rear.png)
Fig. 25 - Roll: Anti-Squat Percentage

![fig26](images/pitch.anti_lift_percent_l_rear.png)
Fig. 26 - Roll: Anti-Lift Percentage (Rear)

![fig27](images/steer.front.camber_angle_l.png)
Fig. 27 - Steering: Camber Angle (Front Left)

![fig28](images/steer.front.ackerman_angle.png)
Fig. 28 - Steering: Ackerman Angle (Front)

![fig29](images/steer.front.steering_ratio.png)
Fig. 29 - Steering: Steering Ratio

### Resulting system

The resulting sytem geometries are shown below in several pictures.

![](images/optimized-front.png)
Fig. 30 - Optimized Suspension: Front View

![](images/optimized-iso.png)
Fig. 31 - Optimized Suspension: Isometric View

![](images/optimized-side.png)
Fig. 31 - Optimized Suspension: Side View

![](images/optimized-top.png)
Fig. 33 - Optimized Suspension: Top View

![](images/optimized-front_axle-front.png)
Fig. 34 - Optimized Suspension: Front axle on front view

![](images/optimized-rear_axle-front.png)
Fig. 35 - Optimized Suspension: Rear axle on front view

### Statistical results

The optimization statistical results are shown below.

![](images/setup07_donut_plot.png)
Fig. 36 - Average fitness distribution per objective of the final population

![](images/optimization_log_2021-08-09_15-25-50.txt_convergence_chart.png)
Fig. 37 - Convergence statistics

