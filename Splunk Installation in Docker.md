# Splunk Installation in Docker

**1.Create new AWS server (Linux)**

**2.Install Docker Engine on RHEL (s390x)**

Refere: (https://docs.docker.com/engine/install/rhel/)

# Installation methods:

**3.Set up the repository:**

* *Install the yum-utils package (which provides the yum-config-manager utility) and set up the repository.* *

```bash
sudo yum install -y yum-utils
```

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
```

**4.Install Docker Engine, containerd, and Docker Compose:**

```bash
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

**5.Start Docker:**

```bash
sudo systemctl start docker
```

**6.Verify that the Docker Engine installation is successful by running the hello-world image.**

```bash
sudo docker run hello-world
```

**7.Download the splunk image to your local Docker engine:**

```bash
docker pull splunk/splunk:latest
```

**8.Use the following command to start a single instance of the Splunk:**

* *Specify a custom SPLUNK_PASSWORD - be sure to replace <password> with any string that conforms to the Splunk Enterprise password requirements.* *

```bash
docker run -d -p 8000:8000 -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=<password>" --name splunk splunk/splunk:latest
```

* *After the container starts up successfully and enters the "healthy" state, you should be able to access SplunkWeb at http://localhost:8000 with admin:<password>.* *
