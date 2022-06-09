# UR LabVIEW Interface
_Unlock the testing potential of your Universals Robot with the power of LabVIEW!_

The UR LabVIEW Interface is an open-source LabVIEW API toolkit and dashboard application from the test automation experts at Sub-Zero Group, Inc. Bring collaborative automation to your LabVIEW architected test systems using out of the box VI’s for controlling Universal Robot’s line of six-axis robots.

Leveraging the dashboard server client interface, the UR LabVIEW Interface code base includes a fully featured dashboard to control your robot in development or lab environments (very useful for developing and debugging applications) as well as a full API toolkit to use in your custom test applications.

## Features
- A standalone dashboard to control your robot and run custom program sequences
- An extensive API toolkit to develop custom test applications
- An object-oriented design with compatibility across e-series and cb-series robots
- Plug and play VI for loading and playing programs while monitoring robot status

## System Requirements
- LabVIEW 2019 or newer
- Can be saved for previous version on request

## Disclaimers
- Software was developed on an E-Series robot, however, code was designed with consideration for CB-Series robots and should be extensible
- Software was developed for company specific objectives and has been used in limited applications. As such, some bugs or nuiances may appear in your robot installation or application

## Getting Started

### Configuring Robot for Remote Control
- The UR LabVIEW Interface heavily relies upon the Dashboard Server Client Interface. In order to use this client interface, the network settings for the robot must be configured and remote control must also be enabled
- For more information on the Dashboard Server and other client interfaces, please refer to the UR Support Article [DASHBOARD SERVER E-SERIES, PORT 29999](https://www.universal-robots.com/articles/ur/dashboard-server-e-series-port-29999/)
- Configure network settings and enable remote control
![Configure Robot Network Settings](documentation/images/robot-network-settings.png)
- Ping the robot to ensure the destination is reachable from your host PC

> If you are unable to establish a connection with your robot, check your Firewall settings. Firewall may need to be disabled to allow bi-directional communication with your PC

### Configure Settings File
1. Open the settings ini file in the root directory of the project with a text editor
2. Configure settings for your robot and preferences

| Settings | Data Type | Hints |
| ------ | ------ | ------ |
| Robot | String | E-Series or CB-Series |
| Robot IP Address | String | Must match IP address in Network settings of robot
| Socket IP Address | String | IP Address of host socket (optional)
| Robot Logging | Boolean | Enable or disable logging of robot events
| TCP Logging | Boolean | Enable or disable logging of each TCP command
| Use SFTP Program List | Boolean | Enable import of program list from robot using SFTP
| Fault Program | String | Robot Program to Use in Fault Conditions (do not include urp file extension)

### Running from LabVIEW Project
Fully development version of LabVIEW is required to open the LabVIEW project
1. Open the UR LabVIEW Interface lvproj in the root directory of the repository
2. Open the UR LabVIEW Interface VI
3. Press the Run arrow

### Running Executable
1. Double click the UR LabVIEW Interface exe in the root directory of the project

## Using the UR LabVIEW Interface
Press the Connect button to establish a network connection with the robot and load dashboard interfaces
![Connect to Robot](documentation/images/connect-robot.png)

### Overview of Interfaces
![Dashboard Overview](documentation/images/dashboard-overview.png)

#### Operation Interface
Used to send high level robot operation commands. Buttons are dynamically enabled and disabled based on the current robot operational status

> Please note, when changing from automatic to remote control mode, the robot TCP connection needs to be reset. A popup will appear prompting you to disconnect then reconnect the robot

![Operation Interface](documentation/images/operation-interface.png)

#### Command Interface
Used to send custom dashboard server commands. A command list is loaded based on the polyscope version of the robot and the compatible commands for that version. Please note, some commands require the robot to be in remote control mode and the send button is disabled for those commands when the robot is in another mode

![Command Interface](documentation/images/command-interface.png)
![Command Interface Command List](documentation/images/command-interface-commands.png)

#### Program Interface
Used to play a single program or build a queue of programs to be played in sequence. Programs can either be loaded from a user defined list in the Settings file

![Program List](documentation/images/settings-program-list.png)

Or by enabling SFTP in the settings file and loading programs directly from the robot

`Use SFTP Program List = "TRUE"`

User can play a single program by selecting a program in the program list and pressing play, or they can build a custom queue of programs to execute in sequence. Queues can be saved and are stored in a flat file in the appData directory so they can be loaded later, even if the software is closed and reopened

> Programs are executed in the Program Controller to ensure a program completes execution before the next program begins in the queue

![Program Interface](documentation/images/program-interface.png)

#### Program Controller
The Program Controller is the cornerstone API used to load, play, and monitor status of a robot program. This VI monitors status of both the robot and program to ensure programs are executed to completion and no errors occur within the program or robot

![Program Controller](documentation/images/settings-program-list.png)

##### Fault Recovery
==under development==

#### Socket Interface
The socket interface can be used to stream data from the robot to PC over a socket connection
- Reference the [Socket Demo Example](documentation/examples/SocketDemo.urp) on how to structure the robot program
- LabVIEW Interface must be running before the socket is opened on the robot
- Data is collected upon program completion

![Socket Interface](documentation/images/socket-interface.png)

## How to Get Help
- The documentation for this project is actively under development. If you have questions about how to use the code, please use submit a question on the  [Question and Anwser Page](https://github.com/cfearing/URLabVIEWInterface/discussions/categories/q-a)
- If you find any issues or bugs with the code, please submit them on the [Issues Page](https://github.com/cfearing/URLabVIEWInterface/issues)
- For other general inquiries feel free to reach out to [Chase Fearing](https://www.linkedin.com/in/chase-fearing-51376265/), architect of the project

## Known Issues
- When connected to the UR LabVIEW Interface and you change operational modes on the teach pendant the TCP connection is occassionaly lost and it causes repeated errors. In this case you need to disconnect then reconnect

## License
- [MIT License Copyright (c) 2022 Sub-Zero Group, Inc.](LICENSE)