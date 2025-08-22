# physiquant__unit variable naming convention
The physiquant__unit variable naming convention for physical quantities in computer code encodes units as a postfix after a double underscore, using metric prefixes with proper capitalization, single underscores to separate compound units, and negative exponents for 'per' units in scientific notation preceded by an underscore.

## Table of contents
* [Motivation](#motivation)
* [Rules](#rules)
* [Examples](#examples)
* [Status](#status)
* [License](#license)
* [Credits](#credits)
* [References](#references)

## Motivation

In the energy transition, physics is everywhere. Correctly handling *units* in code is essential to avoid bugs and misinterpretations. History has shown how costly unit mix-ups can be — for instance, [NASA’s Mars Climate Orbiter (1999) was lost due to a mix-up in units](https://mars.nasa.gov/mars-exploration/missions/polar-lander/).  

In energy software development, the same risks apply on a smaller scale: a megawatt (MW) wind turbine is vastly different from a milliwatt (mW) device. Mislabeling can lead to incorrect conclusions. To reduce this risk, and partly following the advice from [Naming Things in Code - YouTube](https://www.youtube.com/watch?v=-J3wNP6u5YU&t=156s), we propose a clear naming convention for encoding units directly in variable names.

**NB:** We are aware of the scientific field of [dimensional analysis](https://en.wikipedia.org/wiki/Dimensional_analysis) and libraries that may help with dimension checking of physical quantities in your code, e.g. [pint](https://pint.readthedocs.io) (Python), [SI](https://github.com/bernedom/SI) (C++), but have not yet found (the time to develop) reliable ways of including these in our GEKKO-based analysis code.

## Rules

- Use a double underscore (`__`) as a prefix for the unit, and attach the whole as as a postfix after the variable name.
- Use **metric prefix symbols** (k, m, M, G) and units with proper capitalization (Hz, W, s).
- For programming languages without Unicode support, use `u` instead of `µ`.
- For **compound units**, separate factors by a single underscore (`_`); do *not* use multiplication signs.
- Attach **positive exponents** directly after the unit (omit `1`), e.g. `m2` for suqare meters.
- For **reciprocal notation**, use negative exponents with a preceding single underscore (`_`), e.g. `m_s_2`.
- Avoid percentages (`%`). Express as fractions and end variable names with `__0` (suggesting unit^0).  
- For **dimensionless metrics**, prefer an explicit "Watt per Watt" (`__W0`) or similar, which is more informative than `__0`.
- For **cumulative values** (e.g. smart meter readings), use `_cum` before the unit (see example below).
- For **categorical variables** (strings), use `__str`.

## Examples

- Acceleration in m/s²:  
  `acceleration__m_s_2`

- Smart meter reading of electricity use in kWh:  
  `e_use_cum__kWh`

- Efficiency of a boiler, based on the higher heating value (HHV):  
  `eta_boiler_hhv__W0`  
  Here, `eta` denotes efficiency, `_hhv` specifies the reference basis (higher heating value), and `__W0` indicates a *dimensionless quantity* expressed as *Watt per Watt*. For example, an efficiency of 0.95 means 0.95 W useful output per 1 W input.

## Status
Project is: _in progress_

## License
This data is made available under the [CC BY 4.0](./LICENSE.md) by the [Research group Energy Transition, Windesheim University of Applied Sciences](https://windesheim.nl/energietransitie) 

## Credits

Author: 
* Henri ter Hofte · [@henriterhofte](https://github.com/henriterhofte) · Twitter [@HeNRGi](https://twitter.com/HeNRGi)

## References

- *Naming Things in Code* – [YouTube](https://www.youtube.com/watch?v=-J3wNP6u5YU&t=156s).  
- Metric prefix symbols and rules – [Wikipedia: Metric prefix](https://en.wikipedia.org/wiki/Metric_prefix). 
- [pint](https://github.com/hgrecco/pint), by Hernán E. Grecco et al., licensed under the [BSD license](https://github.com/hgrecco/pint/blob/master/LICENSE).  
- [SI](https://github.com/bernedom/SI), by Dominik Berner, licensed under the [MIT license](https://github.com/bernedom/SI/blob/main/LICENSE).  


