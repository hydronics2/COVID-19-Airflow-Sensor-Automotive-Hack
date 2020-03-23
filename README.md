# Airflow - Sensor Automotive Hack

## Project Description ([from Helpful Engineering](https://www.helpfulengineering.org/))
The intent here is to create a monitoring device, based on a mass airflow meter, that can be used when splitting a ventilator into two or more patients. This will allow staff to monitor individual patients while being controlled by one device in extreme situations where the number of ventilators are not enough to handle the number of patients. The readout should be visible locally on the device and there may need to be parameters input by staff to create a safe operating range and to possibly create alarms when the system is measuring an out of range parameter.


### [Project Requirements](https://docs.google.com/document/d/17Ps910A2vRwnM4EM6F-71GNG1XNa0PaeImd53F7428c/edit?usp=sharing)

This is a quick study of using an inexpensive off-the-shelf automotive airflow type sensor.

Reading from an automotive mass airflow sensor using a microController 12bit ADC, 20ms interval

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/01mass_airflow_sensor.PNG)
[Picture mass air flow sensor](https://www.aliexpress.com/i/33021814341.html)

Initial reading trying to inhale/exhale into the 3” tube was poor. Only medium to large breaths would trigger outputs to the ADC.
12 bit ADC => 4096
Only big breaths trigger… read ~200-350 ADC with large breadth


[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/02mass_airflow_sensor.PNG)
Modified Tube within a Tube
Modified the tube diameter to 1.75” using a paper towel roll
[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/03mass_airflow_sensor.PNG)

Big breaths adc peak 900, 0.725volts
Medium breaths peak at ~600
Smallest breath I can take ~400
….. Giant forceful breaths.. I get dizzy after a few… gets up to ~3000 (2.4volts)

I calibrated the sensor using an estimated 430mL for a medium breath. Integrating under the curve for each breath gives an estimated volume.
[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/04mass_airflow_sensor.PNG)

Notes:
- Not sure why the exhales are so noisy. It has something to do with the flow rates being below spec in that direction
- The inhales are actually the opposite direction as the arrow on the sensor body. I tried it both ways and at the flow rates we’re trying to measure, there is more sensitivity in the opposite direction of the intended airflow..
- Reducing the tube diameter even farther (from 1.75” to ~1”) will increase sensitivity with likely no downsides.
- There is time omitted between the inhales and the exhales on the above graph (the ADC was only triggering above a threshold)
- 300-400mL is actually very little volume! That’s the same amount of space as a 1” tube x 18” long. So the air passing through the sensor will likely not get to the patient’s lungs for two or three inhales.

Summary Results and guesses
- Using this sensor or something similar and reducing the diameter of the tube to meet the required sensitivity seems promising.
- Need an airflow sensor to calibrate an airflow sensor. Calibration will need to happen over low, medium, and high air volumes and possibly for each individual sensor produced.
- I’m guessing the accuracy will depend on the sensor selection, tube diameter and placement in the tube. Once calibrated, this current test jig (with the large 1.75” diameter body) is probably +/- 40mL.
- If the diameter of the tube remains 1” or greater, the flow rates will remain low, and I’m guessing inlet and exit conditions ( greater than 2”) to the sensor are going to be negligible


Excel Data Here

Mass Airflow Sensor
Purchased locally [here](https://www.oreillyauto.com/detail/b/blue-streak-electronics-5882/engine-sensors---emissions-25132/engine-sensors-25049/mass-air-flow-sensor-meter-12040/2c278c9432b0/blue-streak-electronics-mass-air-flow-sensor-new/mf21041n/6102972?q=mf21041n&pos=0) for $57, Blue Streak #MF21041N
Sensor type: hot wire anemometer (guessing here)
This MAF sensor is also found under these part numbers OK5771321 8ET009142441 AMMA-751 AMMA751 0891067
Also on aliexpress for ~$22 [https://www.aliexpress.com/i/33021814341.html](https://www.aliexpress.com/i/33021814341.html)

Pinout
Some models have the pin numbers printed on the body
Pin 1 Ground
Pin 2 Signal
Pin 3 Power 7.5-12 volts, 76ma
[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/05mass_airflow_sensor.PNG)



[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/06mass_airflow_sensor.PNG)
Picture. Final test setup

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/07mass_airflow_sensor.PNG)
Picture. Decreased the diameter to 1.75”

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/08mass_airflow_sensor.PNG)
[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/09mass_airflow_sensor.PNG)

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/10mass_airflow_sensor.PNG)
Picture. removing the straightening vanes

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/11mass_airflow_sensor.PNG)

[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/12mass_airflow_sensor.PNG)
[foo](https://github.com/hydronics2/COVID-19-Airflow-Sensor-Automotive-Hack/blob/master/pics/13mass_airflow_sensor.PNG)
