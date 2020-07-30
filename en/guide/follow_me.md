# Follow Me

The [Follow Me](../api_reference/classmavsdk_1_1_follow_me.md) class is used to engage the PX4 [Follow Me Mode](https://docs.px4.io/master/en/flight_modes/follow_me.html) (multicopter only). 
In this mode a copter will automatically yaw to face and follow a user at a specified position and distance.

The API is used to supply the position(s) for the [target](../api_reference/structmavsdk_1_1_follow_me_1_1_target_location.md) and the relative [follow position](../api_reference/structmavsdk_1_1_follow_me_1_1_config.md) of the vehicle. 
Applications must get target position information from the underlying platform (or some other source). The location APIs for supported platforms are listed below:
- Android: [Location](https://developer.android.com/reference/android/location/Location.html)
- Apple: [Core Location Framework](https://developer.apple.com/documentation/corelocation)
- Windows: [Windows.Devices.Geolocation](https://docs.microsoft.com/en-us/uwp/api/Windows.Devices.Geolocation)

> **Warning** Running *QGroundControl* at the same time as the SDK *Follow Me* may result in unpredictable behaviour as both send position updates. 
> You **must** ensure that *GSC Position Streaming* is disabled. 
> Use the latest *QGC Daily Build* and ensure that the **[Application Setting > General](https://docs.qgroundcontrol.com/en/SettingsView/General.html) > Miscellaneous > Stream GCS Position** is set to *Never*.

## Create the Plugin

> **Tip** `FollowMe` objects are created in the same way as other SDK plugins.
  General instructions are provided in the topic: [Using Plugins](../guide/using_plugins.md).

The main steps are:

1. Link the plugin library into your application. 
   Do this by adding `mavsdk_follow_me` to the `target_link_libraries` section of the app's *cmake* build definition file

   ```cmake
   target_link_libraries(your_application_name
     mavsdk
     ...
     mavsdk_follow_me
     ...
   )
   ```
1. [Create a connection](../guide/connections.md) to a `system`. 
   For example (basic code without error checking):
   ```
   #include <mavsdk/mavsdk.h>
   Mavsdk dc;
   ConnectionResult conn_result = dc.add_udp_connection();
   // Wait for the system to connect via heartbeat
   while (!dc.is_connected()) {
      sleep_for(seconds(1));
   }
   // System got discovered.
   System &system = dc.system();
   ```
1. Create a shared pointer to an instance of `FollowMe` instantiated with the `system`: 
   ```
   #include <mavsdk/plugins/follow_me/follow_me.h>
   auto follow_me = std::make_shared<FollowMe >(system);
   ```

The `follow_me` pointer can then used to access the plugin API (as shown in the following sections).

## Set the Follow Configuration

By default the vehicle will follow directly behind the target at a height and distance of 8 metres. 
You can (optionally) call [set_config()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1aa76aab9a21bc3ae475bee6a55c0e4d30) at any time to specify a different height, follow distance, relative position (front left/right/centre or behind) and responsiveness to target movements.

The code fragment below shows how to set the configuration:
```cpp
// configure follow me behaviour
FollowMe::Config config;
config.min_height_m = 12.f;  // Minimum height
config.follow_distance_m = 20.f;  // Follow distance
config.responsiveness = 0.2f;  // Higher responsiveness
config.follow_direction = FollowMe::Config::FollowDirection::FRONT;  //Follow from front-centre

// Apply configuration
FollowMe::Result config_result = follow_me->set_config(config);
if (config_result != FollowMe::Result::SUCCESS) {
    // handle config-setting failure (in this case print error)
    std::cout << "Setting configuration failed:" << FollowMe::result_str(config_result) << std::endl;
}
```

The [get_config()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1aca2e599cd6fb889b9f80dc7a9da57ee9) method is provided to get the current configuration:
```cpp
auto curr_config = follow_me->get_config();
```

## Following a Target

To start and stop following a target, call [start()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1a4b6ae3ec1ff07d8b3a79038e04992003) and [stop()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1a202a7b9edf56d9b883c974a09c14ba7d), respectively - `start()` puts the vehicle into [Follow-Me mode](https://docs.px4.io/master/en/flight_modes/follow_me.html) and `stop()` puts it into [Hold mode](https://docs.px4.io/master/en/flight_modes/hold.html).

Use [set_target_location()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1a1a99e282472235f726bfde430873ffd5) to set the target position(s) for the vehicle to follow (the app typically passes its host's current position, which it would obtain using OS-specific methods). 
This can be called at any time, but messages will only be sent once following is started. 
The plugin automatically resends the last set position at the rate required by the autopilot/flight mode (1 Hz). 

> **Note** Typically you would call `set_target_location()` before or shortly after starting the mode. If you call `start()` without having set any target location, or if the connection is broken, the vehicle will climb to minimum altitude (if needed) and remain in the mode waiting for messages. 

```cpp
// Start following
FollowMe::Result follow_me_result = follow_me->start();
if (follow_me_result != FollowMe::Result::SUCCESS) {
    // handle start failure (in this case print error)
    std::cout << "Failed to start following:" << FollowMe::result_str(follow_me_result) << std::endl;
}


// Get target position from underlying platform and supply to vehicle. 
//   For this example we just show one point being set (instead of a stream).
follow_me->set_target_location({ 47.39776569, 8.54553292, 0.f, 0.f, 0.f, 0.f });


// Stop following
follow_me_result = follow_me->stop();
if (follow_me_result != FollowMe::Result::SUCCESS) {
    // handle stop failure (in this case print error)
    std::cout << "Failed to stop following:" << FollowMe::result_str(follow_me_result) << std::endl;
}
```

The last location that was set can be retrieved using [get_last_location()](../api_reference/classmavsdk_1_1_follow_me.md#classmavsdk_1_1_follow_me_1af2a1af346ee2fa7761b58b406e9e6e0c).
Before a target position is first set this API will return `Nan`.



## Further Information

Additional information/examples for the Follow Me API are linked below:

* [Example:Follow Me Mode](../examples/follow_me.md)
* Integration tests:
  * [follow_me.cpp](https://github.com/mavlink/MAVSDK/blob/{{ book.github_branch }}/src/integration_tests/follow_me.cpp)
