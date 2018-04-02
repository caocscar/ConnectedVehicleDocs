# Events

## ExteriorLightsEvents

8-bit string|Condition|Detailed Description
---|---|---
00000000|allLightsOff|All exterior lights are off.
00000001|lowBeamHeadLightsOn|Low beam headlights are on.
00000010|highBeamHeadLightsOn|High beam headlights are on.
00000100|leftTurnSiganlOn|Left turn signal is on.
00001000|righTurnSignalOn|Right turn signal is on.
00001100|hazardSignalOn|Hazard signal is on.
00010000|automaticLightControlOn|Lights are on due to automatic light control.
00100000|daytimeRunningLightsOn|Day time running lights are on.
01000000|fogLightOn|Fog lights are on.
10000000|parkingLightsOn|Parking lights are on.       

## SteerAngleEvents

This field contains a value to be converted to degrees to communicate steer angle.  
These values have to be converted before the steering wheel angle can be determined. 
The LSB units = 1.5 degrees and entries in this field have a range of -126 to +127, 
which facilitates steering angles between -/+189 degrees and a value signifying that the steering angle is unavailable.  

For example:
- 0 = +1.5 degrees
- -126 = -189 degrees and beyond
- +126 = +189 degrees and beyond
- +127 = unavailable steering angle

More generally, for values between 0 and 126 you simply multiply by 1.5 degrees.
However for value between 129 and 255, maskoff the highest bit (which is being used as a sign bit) by doing a bitwise AND with a value of 127.
Then swap the remaining bit values by doing a bitwise exclusive OR with a value of 127 and then multiply by -1.5.

## ThrottlePositionEvents

This field details the relative position of the throttle over a given trip.
The range of the variable is [0,100]

## WiperStatusFrontEvents

Value|Condition|Detailed Description
---|---|---
0|Unavailable|The status of the vehicle wiper is unavailable or the vehicle is not equipped with the wiper sensor status.
1|Off|Front wipers are not activated.
2|Intermittent|Front wipers are operated at an intermittent frequency.
3|Low|Front wipers are operated at a low frequency.
4|High|Front wipers are operated at a high frequency.
126|Washer in Use|Wipers are active due to the use of the washer fluid.
127|Automatic Present|The wipers have the ability to be automatically turned on.
