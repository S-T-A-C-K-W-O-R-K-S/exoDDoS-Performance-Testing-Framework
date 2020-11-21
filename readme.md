### exoDDoS (CBPm Implementation)
Enterprise-Grade Python Load/Performance Testing Framework

***

### Quick Start

1. navigate to the exoDDoS directory, if not already in that context
2. install the exoDDoS requirements by executing `pip install -r requirements.txt`
3. execute `locust --config exoddos.conf` to launch the framework

***

### Run Via Docker

> One-Time Commands

1. `docker build -t exoddos:1.5.1 .`
2. `docker run -it --name exoddos -p 5557:5557 -p 8089:8089 exoddos:1.5.1`

> Reuse exoDDoS Container

1. `docker start -ai exoddos`
2. `docker stop exoddos`

> Utility Docker Commands

- list all local images: `docker images --all`
- list all local containers: `docker ps --all`

> Run As Debug User

It is possible to run exoDDoS as a single ephemeral user, for debugging purposes, which overrides the credentials file referenced in the codebase.

To do so from a Docker container, append the `-e debug-user="USERNAME"` and `-e debug-pass="PASSWORD"` flags while executing the run command for the Docker container.

Running exoDDoS as a debug user without Docker requires setting a pair of environment variables for the current terminal session, however achieving this depends on the shell in use. For instance, in PowerShell, the syntax would be `$ENV:debug-user="USERNAME"` and, respectively, `$ENV:debug-pass="PASSWORD"`.

> Run With GrayLog Integration Support

To integrate with GrayLog from a Docker container, append the `-e use-graylog="true"`, `-e graylog-ip="IP"` and `-e graylog-port="PORT"` flags while executing the run command for the Docker container.

***

### Troubleshooting

> Clean Installation

1. upgrade PIP to the latest version by executing `pip install --upgrade pip`
2. make a backup of the installed PIP packages by executing `pip freeze > snapshot.txt`
3. uninstall all PIP packages by executing `pip uninstall -r snapshot.txt -y`
4. navigate to the exoDDoS directory, if not already in that context
5. install the exoDDoS requirements by executing `pip install -r requirements.txt`

> Update Requirements

1. upgrade PIP to the latest version by executing `pip install --upgrade pip`
2. make a backup of the installed PIP packages by executing `pip freeze > snapshot.txt`
3. uninstall all PIP packages by executing `pip uninstall -r snapshot.txt -y`
4. install the latest version of locust by executing `pip install locust`
5. navigate to the exoDDoS directory, if not already in that context
6. save all the freshly installed PIP packages as the new requirements by executing `pip freeze > requirements.txt`

*Updating the requirements as per the steps above will convert the requirements file to UCS-2 LE BOM (UNICODE) format so make sure to convert it back to UTF-8 without BOM (ASCII) format, otherwise some GIT clients will see it as a binary file rather than a text file and won't be able to properly resolve the deltas. Alternatively, update the requirements by executing `pip freeze | Out-File -Encoding ASCII requirements.txt`.*

> Prune All Local Docker Data

To start fresh in Docker, execute `docker system prune --all --volumes` and then type `y` when prompted to. Make sure to read carefully what you are pruning, as this will delete all stopped containers, all networks not used by at least one container, all volumes not used by at least one container, all images without at least one container associated to them and all build cache.

> Accessing The WEB UI

By default, the WEB UI runs on `http://:8089` which makes `http://localhost:8089` available even when running exoDDoS from within a Docker container. Setting the `--web-host` config flag for the framework to a custom IP address may require additional Docker image configuration in order to be able to access the WEB UI for an instance of exoDDoS running inside a Docker container.
