# Load and Stress Testing Tools

### K6:

K6 is a n opensource tool that lets us use it to easily write load testing scripts in JavaScript. [1]



##### Installation: 

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
echo "deb https://dl.bintray.com/loadimpact/deb stable main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install k6
```





### Locust:

Locust is an easy to use Python load testing framework that lets us simulate a high usage on different endpoints of our cluster



##### Installation:

- You need python3 and pip on your system

```bash
pip install locust
```





Apache JMeter:







## Sources:

[1] https://k6.io/docs/

[2] https://locust.io/