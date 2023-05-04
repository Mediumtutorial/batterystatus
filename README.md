In ReactJS, you can get the device's battery status by using the Battery Status API, which provides information about a device's battery charge level and charging state but sometimes that causes an issue as many browsers don't support that and it throws an error, so to make it easy we will use a hook from react-use package to get device battery status.
React-use is a popular library that contains reusable hooks for ReactJS. The useBattery hook is one of the most helpful hooks in this library since it allows you to easily retrieve the battery state of the device your application is running on. In this tutorial, we'll look at how to use ReactJS's useBattery hook.
Requirements
react-use

Step 1: Install React-use
Before we get started with the useBattery hook, we must first install the React-use package. To do so, open your terminal and navigate to the ReactJS application's root directory. Then execute the following command.
npm install react-use
Step 2: Import useBattery hook
To use the useBattery hook, we need to import it from the react-use library. Here's an example
import { useBattery } from 'react-use';
Step 3: Use useBattery hook
Once the useBattery hook has been imported, we can use it inside a functional component. The useBattery hook returns an object that contains several properties, including the battery level, charging state, charging time, and discharging time. Here's an example of how to use the useBattery hook.
import React from "react";
import { useBattery } from "react-use";

function App() {
  // Calling useBattery hook
  const battery = useBattery();

  // Destructuring battery properties
  const { isSupported, level, charging, dischargingTime, chargingTime } =
    battery;

  //Check if browser support Battery API
  if (!isSupported) {
    return (
      <div>
        <strong>Battery sensor</strong>: <span>Not supported</span>
      </div>
    );
  }

  return (
    <div>
      {/* Display Battery Charge Percentage */}
      <strong>Charge level</strong>:&nbsp;&nbsp;{" "}
      <span>{(level * 100).toFixed(0)}%</span> <br />
      {/* Display Whether Device is charging or not */}
      <strong>Charging</strong>:&nbsp;&nbsp;{" "}
      <span>{charging ? "Yes" : "No"}</span> <br />
      {/* Display Device Charging time */}
      <strong>Charging time</strong>:&nbsp;&nbsp;
      <span>{chargingTime ? chargingTime : "Finished"}</span> <br />
      {/* Display Device Discharging time */}
      <strong>Discharging time</strong>:&nbsp;&nbsp;{" "}
      <span>{dischargingTime}</span>
    </div>
  );
}

export default App;
