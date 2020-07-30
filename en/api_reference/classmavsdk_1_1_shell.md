# mavsdk::Shell Class Reference
`#include: shell.h`

----


<ul>
<li><p>Allow to communicate with the vehicle's system shell. </p></li>
</ul>


## Public Types


Type | Description
--- | ---
enum [Result](#classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8) | Possible results returned for shell requests.
std::function< void([Result](classmavsdk_1_1_shell.md#classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8))> [ResultCallback](#classmavsdk_1_1_shell_1a4937843446c999606349ad438f8d682d) | Callback type for asynchronous [Shell](classmavsdk_1_1_shell.md) calls.
std::function< void(std::string)> [ReceiveCallback](#classmavsdk_1_1_shell_1adfa64ede96967ae1ab5a5ecd83032dbb) | Callback type for subscribe_receive.

## Public Member Functions


Type | Name | Description
---: | --- | ---
&nbsp; | [Shell](#classmavsdk_1_1_shell_1a31a80044ee4822e8b9ac1c515b0eea90) ([System](classmavsdk_1_1_system.md) & system) | Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).
&nbsp; | [~Shell](#classmavsdk_1_1_shell_1a26b0e0d6a00d89c3d22c0f8a580c54c4) () | Destructor (internal use only).
&nbsp; | [Shell](#classmavsdk_1_1_shell_1a7fdf25f0db49675a24c6ce61be9f82b5) (const [Shell](classmavsdk_1_1_shell.md) &)=delete | Copy constructor (object is not copyable).
[Result](classmavsdk_1_1_shell.md#classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8) | [send](#classmavsdk_1_1_shell_1a7b39022ce3be914eec82b53a76d19bc7) (std::string command)const | Send a command line.
void | [subscribe_receive](#classmavsdk_1_1_shell_1aa7e47ad1ce0f35e82701bd1811598ee1) ([ReceiveCallback](classmavsdk_1_1_shell.md#classmavsdk_1_1_shell_1adfa64ede96967ae1ab5a5ecd83032dbb) callback) | Receive feedback from a sent command line.
const [Shell](classmavsdk_1_1_shell.md) & | [operator=](#classmavsdk_1_1_shell_1a492f8b2e36ef2468522bfd0f51f4b9b8) (const [Shell](classmavsdk_1_1_shell.md) &)=delete | Equality operator (object is not copyable).


## Constructor & Destructor Documentation


### Shell() {#classmavsdk_1_1_shell_1a31a80044ee4822e8b9ac1c515b0eea90}
```cpp
mavsdk::Shell::Shell(System &system)
```


Constructor. Creates the plugin for a specific [System](classmavsdk_1_1_system.md).

The plugin is typically created as shown below: 

```cpp
auto shell = std::make_shared<Shell>(system);
```

**Parameters**

* [System](classmavsdk_1_1_system.md)& **system** - The specific system associated with this plugin.

### ~Shell() {#classmavsdk_1_1_shell_1a26b0e0d6a00d89c3d22c0f8a580c54c4}
```cpp
mavsdk::Shell::~Shell()
```


Destructor (internal use only).


### Shell() {#classmavsdk_1_1_shell_1a7fdf25f0db49675a24c6ce61be9f82b5}
```cpp
mavsdk::Shell::Shell(const Shell &)=delete
```


Copy constructor (object is not copyable).


**Parameters**

* const [Shell](classmavsdk_1_1_shell.md)&  - 

## Member Typdef Documentation


### typedef ResultCallback {#classmavsdk_1_1_shell_1a4937843446c999606349ad438f8d682d}

```cpp
using mavsdk::Shell::ResultCallback =  std::function<void(Result)>
```


Callback type for asynchronous [Shell](classmavsdk_1_1_shell.md) calls.


### typedef ReceiveCallback {#classmavsdk_1_1_shell_1adfa64ede96967ae1ab5a5ecd83032dbb}

```cpp
using mavsdk::Shell::ReceiveCallback =  std::function<void(std::string)>
```


Callback type for subscribe_receive.


## Member Enumeration Documentation


### enum Result {#classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8}


Possible results returned for shell requests.


Value | Description
--- | ---
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8a88183b946cc5f0e8c96b2e66e1c74a7e"></span> `Unknown` | Unknown result. 
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8a505a83f220c02df2f85c3810cd9ceb38"></span> `Success` | Request succeeded. 
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8a1119faf72ba0dfb23aeea644fed960ad"></span> `NoSystem` | No system is connected. 
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8a094a6f6b0868122a9dd008cb91c083e4"></span> `ConnectionError` | Connection error. 
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8a0e976dcd18516429d344402e6f5524d3"></span> `NoResponse` | Response was not received. 
<span id="classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8ad8a942ef2b04672adfafef0ad817a407"></span> `Busy` | [Shell](classmavsdk_1_1_shell.md) busy (transfer in progress). 

## Member Function Documentation


### send() {#classmavsdk_1_1_shell_1a7b39022ce3be914eec82b53a76d19bc7}
```cpp
Result mavsdk::Shell::send(std::string command) const
```


Send a command line.

This function is blocking.

**Parameters**

* std::string **command** - 

**Returns**

&emsp;[Result](classmavsdk_1_1_shell.md#classmavsdk_1_1_shell_1a768bfa296ba3309f936f887fb86c9ba8) - Result of request.

### subscribe_receive() {#classmavsdk_1_1_shell_1aa7e47ad1ce0f35e82701bd1811598ee1}
```cpp
void mavsdk::Shell::subscribe_receive(ReceiveCallback callback)
```


Receive feedback from a sent command line.

This subscription needs to be made before a command line is sent, otherwise, no response will be sent.

**Parameters**

* [ReceiveCallback](classmavsdk_1_1_shell.md#classmavsdk_1_1_shell_1adfa64ede96967ae1ab5a5ecd83032dbb) **callback** - 

### operator=() {#classmavsdk_1_1_shell_1a492f8b2e36ef2468522bfd0f51f4b9b8}
```cpp
const Shell& mavsdk::Shell::operator=(const Shell &)=delete
```


Equality operator (object is not copyable).


**Parameters**

* const [Shell](classmavsdk_1_1_shell.md)&  - 

**Returns**

&emsp;const [Shell](classmavsdk_1_1_shell.md) & - 