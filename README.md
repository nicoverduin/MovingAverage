# MovingAverage
Robust library for calculating a moving average. A moving average is an average value based on a predefined set of vales For example a moving average on 3 values is calculated on the last 3 values summed devided by 3. The catch is that the type of variable may be a series of ints or longs or floats or doubles etc. 
This libary allows one to create an object for a moving averages that is determined by the definition parameter.

A moving avarage based on floats would be defined as follows:

```
MovingAverage <float> myMovingAverage(numberOfEntries);
```

Where

<float> means the moving average is calculated based on floats
Other examples would be <unsigned int> or <uint8_t> or <long> of <double>

NumberOfEntries tells the Moving Average on how many values the average is based. Also note that when the moving average starts, there could be insufficient values given to the moving average object. The object keeps track of this. If only one value has been added during calculation the average will of course be based on the single value.


 * Author	: Nico Verduin (nico.verduin@ziggo.nl)
 * Date		: 31-8-2016
 *
 * generic MovingAverage class
 * This is a template class that allows one to create a parametric moving average object.
 * The class will be initialized based on a template parameter (i.e. float, double, int , uint16_t etc)
 * non floating point objects will always return a new moving average based on the same type as
 * it was initialized.
 * Keep in mind that floating point on Arduino has a limitation in accuracy up to 6-7 digits.
 * If the input for the MA is too lager, intermediate results will lose significant digits causing
 * inaccuracy.
 *
 * functions
 * ---------
 * MovingAverage(uint16_t)		Constructor creating object suitable for the parameterized number of entries
 * ~MovingAverage()				Destructor freeing up unallocated memory
 * T CalculateMovingAverage(T)	Calculate a moving average based on type T (can be any type i.e. float, int etc)
 * 								and returns type T (same as values passed)
 *
 * assert
 * ------
 * Operational guard routine	The library has an assert built in but is turned off under normal conditions.
 * 								However switching this on through #define DEBUG_MODE will ensure that the
 * 								program halts if more memory is requested than available. For example in an
 * 								Arduino UNO Ram is limited to 2K. If you want to do a moving average on 1000
 * 								floating point values this would require (1000 x 4 bytes) = 4000 bytes. The check
 * 								will output an error on the Serial if this occurs.
 *
 * 	using RAM efficiëntly
 * 	---------------------
 * 	If a moving average does not need to stay alive until the Arduino is reset or switch off, use the
 * 	deconstructor (! MovingAverage() to free up Ram.
 * 	This will free up the dynamic allocated internal array of sizeof variable type * number of entries for
 * 	moving average.
 */

