# CoreSpark - Install Spark in Ubuntu Machine

Virtual environment:
-------------------------------------
sudo apt install virtualenv

virtualenv -p /usr/bin/python3.6 .venv

source .venv/bin/activate

Dependencies:
-----------------------------------
pip install boto3

pip install tweepy (if you want to work on tweets)

Execute bash profile to get the env variables
------------------------------------------------
.    ~/.bash_profile

# Install Packages Required for Spark

sudo apt install default-jdk scala git -y

# verify the installed dependencies

java -version; javac -version; scala -version; git --version

# Download and Set Up Spark on Ubuntu

wget https://downloads.apache.org/spark/spark-3.0.1/spark-3.0.1-bin-hadoop2.7.tgz

# Now, extract the saved archive using the tar command:

tar xvf spark-*

# Finally, move the unpacked directory spark-3.0.1-bin-hadoop2.7 to the opt/spark directory.

sudo mv spark-3.0.1-bin-hadoop2.7 /opt/spark

# Use the echo command to add these three lines to .profile:

echo "export SPARK_HOME=/opt/spark" >> ~/.profile
echo "export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin" >> ~/.profile
echo "export PYSPARK_PYTHON=/usr/bin/python3" >> ~/.profile

# Or Add it in the .bash_profile

export SPARK_HOME=/opt/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
export PYSPARK_PYTHON=/usr/bin/python3

source ~/.profile
or
. ~/.bash_profile

# Start Standalone Spark Master Server

start-master.sh

http://127.0.0.1:8080/

# Start Spark Slave Server (Start a Worker Process)

start-slave.sh spark://master:port

start-slave.sh spark://ubuntu1:7077

# start a worker and assign only one CPU core to it, enter this command:

start-slave.sh -c 1 spark://ubuntu1:7077

# start a worker with 512MB of memory, enter this command:

start-slave.sh -m 512M spark://ubuntu1:7077

# Test Spark Shell

spark-shell

# Test Python in Spark

pyspark

## Basic Commands to Start and Stop Master Server and Workers

# To start a master server instance on the current machine, run the command 

start-master.sh

# To stop the master instance started by executing the script above, run:

stop-master.sh

# To stop a running worker process, enter this command:

stop-slave.sh

# Start both master and server instances by using the start-all command:

start-all.sh

# Can stop all instances by using the following command:

stop-all.sh
