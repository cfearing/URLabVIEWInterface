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

## Getting Started

### Configuring Robot for Remote Control
- The UR LabVIEW Interface heavily relies upon the Dashboard Server Client Interface. In order to use this client interface, the network settings for the robot must be configured and remote control must also be enabled
- For more information on the Dashboard Server and other client interfaces, please refer to the UR Support Article [DASHBOARD SERVER E-SERIES, PORT 29999](https://www.universal-robots.com/articles/ur/dashboard-server-e-series-port-29999/)
- Configure network settings and enable remote control
![Configure Robot Network Settings](documentation/images/robot-network-settings.jpg)

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

### Running from LabVIEW Project
Fully development version of LabVIEW is required to open the LabVIEW project
1. Open the UR LabVIEW Interface lvproj in the root directory of the repository
2. Open the UR LabVIEW Interface VI
3. Press the Run arrow

### Running Executable
1. Double click the UR LabVIEW Interface exe in the root directory of the project

## Using the UR LabVIEW Interface


## How to Get Help
- The documentation for this project is actively under development. If you have questions about how to use the code, please use submit a question on the  [Question and Anwser Page](https://github.com/cfearing/URLabVIEWInterface/discussions/categories/q-a)
- If you find any issues or bugs with the code, please submit them on the [Issues Page](https://github.com/cfearing/URLabVIEWInterface/issues)
- For other general inquiries feel free to reach out to [Chase Fearing](https://www.linkedin.com/in/chase-fearing-51376265/), architect of the project

## Features

- Import a HTML file and watch it magically convert to Markdown
- Drag and drop images (requires your Dropbox account be linked)
- Import and save files from GitHub, Dropbox, Google Drive and One Drive
- Drag and drop markdown and HTML files into Dillinger
- Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>