# mavsdk::Param Class Reference
`#include: param.h`

----


Provide raw access to get and set parameters. 


## Public Types


Type | Description
--- | ---
enum [Result](#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df) | Possible results returned for param requests.
std::function< void([Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df))> [ResultCallback](#classmavsdk_1_1_param_1a7047374c38d4220e8709c2b10275f860) | Callback type for asynchronous [Param](classmavsdk_1_1_param.md) calls.

## Public Member Functions


Type | Name | Description
---: | --- | ---
&nbsp; | [Param](#classmavsdk_1_1_param_1a3f15c8d0c238a68cd97a49ba5c3ea1ef) ([System](classmavsdk_1_1_system.md) & system) | Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).
&nbsp; | [~Param](#classmavsdk_1_1_param_1afe3db48e33da2ff7245e41fe0636fdc3) () | Destructor (internal use only).
&nbsp; | [Param](#classmavsdk_1_1_param_1afc29940366bad9212874584f2d6262ce) (const [Param](classmavsdk_1_1_param.md) &)=delete | Copy constructor (object is not copyable).
std::pair< [Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df), int32_t > | [get_param_int](#classmavsdk_1_1_param_1a554099a07baa9e4765824005f47bef94) (std::string name)const | Get an int parameter.
[Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df) | [set_param_int](#classmavsdk_1_1_param_1af8124bae8b4649605a51fe2943ae8414) (std::string name, int32_t value)const | Set an int parameter.
std::pair< [Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df), float > | [get_param_float](#classmavsdk_1_1_param_1ac8efd0381aa1cc2e4461dfb256797619) (std::string name)const | Get a float parameter.
[Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df) | [set_param_float](#classmavsdk_1_1_param_1a58a2f14fbcda2bf73815dbc2a31528bf) (std::string name, float value)const | Set a float parameter.
const [Param](classmavsdk_1_1_param.md) & | [operator=](#classmavsdk_1_1_param_1a4d75b066cb985d3a38cc8221e18aa608) (const [Param](classmavsdk_1_1_param.md) &)=delete | Equality operator (object is not copyable).


## Constructor & Destructor Documentation


### Param() {#classmavsdk_1_1_param_1a3f15c8d0c238a68cd97a49ba5c3ea1ef}
```cpp
mavsdk::Param::Param(System &system)
```


Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).

The plugin is typically created as shown below: 

```cpp
auto param = std::make_shared<Param>(system);
```

**Parameters**

* [System](classmavsdk_1_1_system.md)& **system** - The specific system associated with this plugin.

### ~Param() {#classmavsdk_1_1_param_1afe3db48e33da2ff7245e41fe0636fdc3}
```cpp
mavsdk::Param::~Param()
```


Destructor (internal use only).


### Param() {#classmavsdk_1_1_param_1afc29940366bad9212874584f2d6262ce}
```cpp
mavsdk::Param::Param(const Param &)=delete
```


Copy constructor (object is not copyable).


**Parameters**

* const [Param](classmavsdk_1_1_param.md)&  - 

## Member Typdef Documentation


### typedef ResultCallback {#classmavsdk_1_1_param_1a7047374c38d4220e8709c2b10275f860}

```cpp
using mavsdk::Param::ResultCallback =  std::function<void(Result)>
```


Callback type for asynchronous [Param](classmavsdk_1_1_param.md) calls.


## Member Enumeration Documentation


### enum Result {#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df}


Possible results returned for param requests.


Value | Description
--- | ---
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfa88183b946cc5f0e8c96b2e66e1c74a7e"></span> `Unknown` | Unknown result. 
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfa505a83f220c02df2f85c3810cd9ceb38"></span> `Success` | Request succeeded. 
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfac85a251cc457840f1e032f1b733e9398"></span> `Timeout` | Request timed out. 
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfa094a6f6b0868122a9dd008cb91c083e4"></span> `ConnectionError` | Connection error. 
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfafdf152936dcbf201445440856357f6ac"></span> `WrongType` | Wrong type. 
<span id="classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881dfaa2b5cfc4e45ca036892b3dadc483e655"></span> `ParamNameTooLong` | Parameter name too long (> 16). 

## Member Function Documentation


### get_param_int() {#classmavsdk_1_1_param_1a554099a07baa9e4765824005f47bef94}
```cpp
std::pair<Result, int32_t> mavsdk::Param::get_param_int(std::string name) const
```


Get an int parameter.

If the type is wrong, the result will be `WRONG_TYPE`.


This function is blocking.

**Parameters**

* std::string **name** - 

**Returns**

&emsp;std::pair< [Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df), int32_t > - Result of request.

### set_param_int() {#classmavsdk_1_1_param_1af8124bae8b4649605a51fe2943ae8414}
```cpp
Result mavsdk::Param::set_param_int(std::string name, int32_t value) const
```


Set an int parameter.

If the type is wrong, the result will be `WRONG_TYPE`.


This function is blocking.

**Parameters**

* std::string **name** - 
* int32_t **value** - 

**Returns**

&emsp;[Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df) - Result of request.

### get_param_float() {#classmavsdk_1_1_param_1ac8efd0381aa1cc2e4461dfb256797619}
```cpp
std::pair<Result, float> mavsdk::Param::get_param_float(std::string name) const
```


Get a float parameter.

If the type is wrong, the result will be `WRONG_TYPE`.


This function is blocking.

**Parameters**

* std::string **name** - 

**Returns**

&emsp;std::pair< [Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df), float > - Result of request.

### set_param_float() {#classmavsdk_1_1_param_1a58a2f14fbcda2bf73815dbc2a31528bf}
```cpp
Result mavsdk::Param::set_param_float(std::string name, float value) const
```


Set a float parameter.

If the type is wrong, the result will be `WRONG_TYPE`.


This function is blocking.

**Parameters**

* std::string **name** - 
* float **value** - 

**Returns**

&emsp;[Result](classmavsdk_1_1_param.md#classmavsdk_1_1_param_1afde69c8b60c41e2f21db148d211881df) - Result of request.

### operator=() {#classmavsdk_1_1_param_1a4d75b066cb985d3a38cc8221e18aa608}
```cpp
const Param& mavsdk::Param::operator=(const Param &)=delete
```


Equality operator (object is not copyable).


**Parameters**

* const [Param](classmavsdk_1_1_param.md)&  - 

**Returns**

&emsp;const [Param](classmavsdk_1_1_param.md) & - 