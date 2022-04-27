# dev-setup-java-17<!-- omit in toc -->

Impetus: I wanted to set up Java 17 in Debian 11 via WSL.

- [Prerequisites](#prerequisites)
  - [Debian 11](#debian-11)
- [Steps for Debian 11](#steps-for-debian-11)
- [Steps for Debian 9/10](#steps-for-debian-910)

# Prerequisites

## Debian 11
If you're not already running Debian 11, follow the guide (likely upgrading from Debian 9): [link to guide](wsl-debian9-to-debian11.md).

# Steps for Debian 11

Update:
```bash
sudo apt update
```

Search for Java 17:
```bash
apt-cache search openjdk | grep 17
```

You should see something like this:
```bash
openjdk-17-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-17-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-17-doc - OpenJDK Development Kit (JDK) documentation
openjdk-17-jdk - OpenJDK Development Kit (JDK)
openjdk-17-jdk-headless - OpenJDK Development Kit (JDK) (headless)
openjdk-17-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-17-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-17-jre-zero - Alternative JVM for OpenJDK, using Zero
openjdk-17-source - OpenJDK Development Kit (JDK) source files
```

This means you can install it; do so: 
```bash
sudo apt install openjdk-17-jdk
```

Verify:
```bash
java -version
```

# Steps for Debian 9/10

```bash
sudo apt update
sudo apt -y install wget curl
```

```bash
wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb
```

```bash
sudo apt install ./jdk-17_linux-x64_bin.deb
```

Agree when prompted.

Configure Java environment.
```bash
cat <<EOF | sudo tee /etc/profile.d/jdk.sh
export JAVA_HOME=/usr/lib/jvm/jdk-17/
export PATH=\$PATH:\$JAVA_HOME/bin
EOF
```

To check if you have Java installed on your machine, type the following command:
```bash
source /etc/profile.d/jdk.sh
```

Verify:
```bash
java -version
```