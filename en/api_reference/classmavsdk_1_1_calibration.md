# mavsdk::Calibration Class Reference
`#include: calibration.h`

----


Enable to calibrate sensors of a drone such as gyro, accelerometer, and magnetometer. 


## Data Structures


struct [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md)

## Public Types


Type | Description
--- | ---
enum [Result](#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1) | Possible results returned for calibration commands.
std::function< void([Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1))> [ResultCallback](#classmavsdk_1_1_calibration_1a566676d5803020cfda7a4a9d9f4a0161) | Callback type for asynchronous [Calibration](classmavsdk_1_1_calibration.md) calls.
std::function< void([Calibration::Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1), [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md))> [CalibrateGyroCallback](#classmavsdk_1_1_calibration_1a299f3806f729afc6ed084fa768c74d8a) | Callback type for calibrate_gyro_async.
std::function< void([Calibration::Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1), [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md))> [CalibrateAccelerometerCallback](#classmavsdk_1_1_calibration_1ab154239054db49d3f790e89dd4eef4a2) | Callback type for calibrate_accelerometer_async.
std::function< void([Calibration::Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1), [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md))> [CalibrateMagnetometerCallback](#classmavsdk_1_1_calibration_1a27ac7e84b676d0a74c570586af162bbb) | Callback type for calibrate_magnetometer_async.
std::function< void([Calibration::Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1), [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md))> [CalibrateLevelHorizonCallback](#classmavsdk_1_1_calibration_1a2534503e1ab0b87fc0cb6778392820e3) | Callback type for calibrate_level_horizon_async.
std::function< void([Calibration::Result](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1), [ProgressData](structmavsdk_1_1_calibration_1_1_progress_data.md))> [CalibrateGimbalAccelerometerCallback](#classmavsdk_1_1_calibration_1a3f79f5152573aaf6ce6d3fd1683af6c4) | Callback type for calibrate_gimbal_accelerometer_async.

## Public Member Functions


Type | Name | Description
---: | --- | ---
&nbsp; | [Calibration](#classmavsdk_1_1_calibration_1ac86c794a9ca1043e21b501218346f2b1) ([System](classmavsdk_1_1_system.md) & system) | Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).
&nbsp; | [~Calibration](#classmavsdk_1_1_calibration_1a9bfe7b366c142b90b4f35cb3b2dfda2e) () | Destructor (internal use only).
&nbsp; | [Calibration](#classmavsdk_1_1_calibration_1a8665891ac02e50c2017793af665c5f4f) (const [Calibration](classmavsdk_1_1_calibration.md) &)=delete | Copy constructor (object is not copyable).
void | [calibrate_gyro_async](#classmavsdk_1_1_calibration_1abf9e20bb07dbbaa0c7481f6296a0d35c) ([CalibrateGyroCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a299f3806f729afc6ed084fa768c74d8a) callback) | Perform gyro calibration.
void | [calibrate_accelerometer_async](#classmavsdk_1_1_calibration_1a135a5e5cd76b2a181345a9e90cfd7c77) ([CalibrateAccelerometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1ab154239054db49d3f790e89dd4eef4a2) callback) | Perform accelerometer calibration.
void | [calibrate_magnetometer_async](#classmavsdk_1_1_calibration_1a430fd1aafa1718969400bfcad0bf155a) ([CalibrateMagnetometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a27ac7e84b676d0a74c570586af162bbb) callback) | Perform magnetometer calibration.
void | [calibrate_level_horizon_async](#classmavsdk_1_1_calibration_1a3ae22637db83e8b2a790429affd1965b) ([CalibrateLevelHorizonCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a2534503e1ab0b87fc0cb6778392820e3) callback) | Perform board level horizon calibration.
void | [calibrate_gimbal_accelerometer_async](#classmavsdk_1_1_calibration_1a11cfa1951cd34dca2ac605f15a0e2b35) ([CalibrateGimbalAccelerometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a3f79f5152573aaf6ce6d3fd1683af6c4) callback) | Perform gimbal accelerometer calibration.
void | [cancel](#classmavsdk_1_1_calibration_1affb9d951b770d6684e9b5594c1fb6bef) () const | Cancel ongoing calibration process.
const [Calibration](classmavsdk_1_1_calibration.md) & | [operator=](#classmavsdk_1_1_calibration_1ada12d974bb516745ea67f94c72abf59b) (const [Calibration](classmavsdk_1_1_calibration.md) &)=delete | Equality operator (object is not copyable).


## Constructor & Destructor Documentation


### Calibration() {#classmavsdk_1_1_calibration_1ac86c794a9ca1043e21b501218346f2b1}
```cpp
mavsdk::Calibration::Calibration(System &system)
```


Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).

The plugin is typically created as shown below: 

```cpp
auto calibration = std::make_shared<Calibration>(system);
```

**Parameters**

* [System](classmavsdk_1_1_system.md)& **system** - The specific system associated with this plugin.

### ~Calibration() {#classmavsdk_1_1_calibration_1a9bfe7b366c142b90b4f35cb3b2dfda2e}
```cpp
mavsdk::Calibration::~Calibration()
```


Destructor (internal use only).


### Calibration() {#classmavsdk_1_1_calibration_1a8665891ac02e50c2017793af665c5f4f}
```cpp
mavsdk::Calibration::Calibration(const Calibration &)=delete
```


Copy constructor (object is not copyable).


**Parameters**

* const [Calibration](classmavsdk_1_1_calibration.md)&  - 

## Member Typdef Documentation


### typedef ResultCallback {#classmavsdk_1_1_calibration_1a566676d5803020cfda7a4a9d9f4a0161}

```cpp
using mavsdk::Calibration::ResultCallback =  std::function<void(Result)>
```


Callback type for asynchronous [Calibration](classmavsdk_1_1_calibration.md) calls.


### typedef CalibrateGyroCallback {#classmavsdk_1_1_calibration_1a299f3806f729afc6ed084fa768c74d8a}

```cpp
using mavsdk::Calibration::CalibrateGyroCallback =  std::function<void(Calibration::Result, ProgressData)>
```


Callback type for calibrate_gyro_async.


### typedef CalibrateAccelerometerCallback {#classmavsdk_1_1_calibration_1ab154239054db49d3f790e89dd4eef4a2}

```cpp
using mavsdk::Calibration::CalibrateAccelerometerCallback =  std::function<void(Calibration::Result, ProgressData)>
```


Callback type for calibrate_accelerometer_async.


### typedef CalibrateMagnetometerCallback {#classmavsdk_1_1_calibration_1a27ac7e84b676d0a74c570586af162bbb}

```cpp
using mavsdk::Calibration::CalibrateMagnetometerCallback =  std::function<void(Calibration::Result, ProgressData)>
```


Callback type for calibrate_magnetometer_async.


### typedef CalibrateLevelHorizonCallback {#classmavsdk_1_1_calibration_1a2534503e1ab0b87fc0cb6778392820e3}

```cpp
using mavsdk::Calibration::CalibrateLevelHorizonCallback =  std::function<void(Calibration::Result, ProgressData)>
```


Callback type for calibrate_level_horizon_async.


### typedef CalibrateGimbalAccelerometerCallback {#classmavsdk_1_1_calibration_1a3f79f5152573aaf6ce6d3fd1683af6c4}

```cpp
using mavsdk::Calibration::CalibrateGimbalAccelerometerCallback =  std::function<void(Calibration::Result, ProgressData)>
```


Callback type for calibrate_gimbal_accelerometer_async.


## Member Enumeration Documentation


### enum Result {#classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1}


Possible results returned for calibration commands.


Value | Description
--- | ---
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a88183b946cc5f0e8c96b2e66e1c74a7e"></span> `Unknown` | Unknown result. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a505a83f220c02df2f85c3810cd9ceb38"></span> `Success` | The calibration succeeded. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a10ac3d04253ef7e1ddc73e6091c0cd55"></span> `Next` | Intermediate message showing progress or instructions on the next steps. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1ad7c8c85bf79bbe1b7188497c32c3b0ca"></span> `Failed` | [Calibration](classmavsdk_1_1_calibration.md) failed. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a1119faf72ba0dfb23aeea644fed960ad"></span> `NoSystem` | No system is connected. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a094a6f6b0868122a9dd008cb91c083e4"></span> `ConnectionError` | Connection error. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1ad8a942ef2b04672adfafef0ad817a407"></span> `Busy` | Vehicle is busy. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a3398e12855176d55f43d53e04f472c8a"></span> `CommandDenied` | Command refused by vehicle. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1ac85a251cc457840f1e032f1b733e9398"></span> `Timeout` | Command timed out. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1aa149e85a44aeec9140e92733d9ed694e"></span> `Cancelled` | [Calibration](classmavsdk_1_1_calibration.md) process was cancelled. 
<span id="classmavsdk_1_1_calibration_1a6e1ce7a3a07eb098edc06821d23a8ec1a6d653ef81fcbd6909f17f5f91778b159"></span> `FailedArmed` | [Calibration](classmavsdk_1_1_calibration.md) process failed since the vehicle is armed. 

## Member Function Documentation


### calibrate_gyro_async() {#classmavsdk_1_1_calibration_1abf9e20bb07dbbaa0c7481f6296a0d35c}
```cpp
void mavsdk::Calibration::calibrate_gyro_async(CalibrateGyroCallback callback)
```


Perform gyro calibration.


**Parameters**

* [CalibrateGyroCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a299f3806f729afc6ed084fa768c74d8a) **callback** - 

### calibrate_accelerometer_async() {#classmavsdk_1_1_calibration_1a135a5e5cd76b2a181345a9e90cfd7c77}
```cpp
void mavsdk::Calibration::calibrate_accelerometer_async(CalibrateAccelerometerCallback callback)
```


Perform accelerometer calibration.


**Parameters**

* [CalibrateAccelerometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1ab154239054db49d3f790e89dd4eef4a2) **callback** - 

### calibrate_magnetometer_async() {#classmavsdk_1_1_calibration_1a430fd1aafa1718969400bfcad0bf155a}
```cpp
void mavsdk::Calibration::calibrate_magnetometer_async(CalibrateMagnetometerCallback callback)
```


Perform magnetometer calibration.


**Parameters**

* [CalibrateMagnetometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a27ac7e84b676d0a74c570586af162bbb) **callback** - 

### calibrate_level_horizon_async() {#classmavsdk_1_1_calibration_1a3ae22637db83e8b2a790429affd1965b}
```cpp
void mavsdk::Calibration::calibrate_level_horizon_async(CalibrateLevelHorizonCallback callback)
```


Perform board level horizon calibration.


**Parameters**

* [CalibrateLevelHorizonCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a2534503e1ab0b87fc0cb6778392820e3) **callback** - 

### calibrate_gimbal_accelerometer_async() {#classmavsdk_1_1_calibration_1a11cfa1951cd34dca2ac605f15a0e2b35}
```cpp
void mavsdk::Calibration::calibrate_gimbal_accelerometer_async(CalibrateGimbalAccelerometerCallback callback)
```


Perform gimbal accelerometer calibration.


**Parameters**

* [CalibrateGimbalAccelerometerCallback](classmavsdk_1_1_calibration.md#classmavsdk_1_1_calibration_1a3f79f5152573aaf6ce6d3fd1683af6c4) **callback** - 

### cancel() {#classmavsdk_1_1_calibration_1affb9d951b770d6684e9b5594c1fb6bef}
```cpp
void mavsdk::Calibration::cancel() const
```


Cancel ongoing calibration process.

This function is blocking.

### operator=() {#classmavsdk_1_1_calibration_1ada12d974bb516745ea67f94c72abf59b}
```cpp
const Calibration& mavsdk::Calibration::operator=(const Calibration &)=delete
```


Equality operator (object is not copyable).


**Parameters**

* const [Calibration](classmavsdk_1_1_calibration.md)&  - 

**Returns**

&emsp;const [Calibration](classmavsdk_1_1_calibration.md) & - 