## Getting started With Containerd From Scratch on Ubuntu 18.4 or 20.4

#### There are a very Simple Few Steps to install containerd So If you are a beginner and even if you Don't Know What is Container Runtime then Stick with Me We will play with containerd

Open the Terminal and run the command
```
sudo apt-get install containerd
```
![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648891463761/zpaedZP8q.png)
Then We have to pull the image from the Docker registry
```
sudo ctr image pull docker.io/library/redis:latest
```

![2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648891504428/itZFr2WZ4.png)
List out The List Of Images using the Following command:-
```
sudo ctr images list
```

![3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648891555210/YnnP5VUYt.png)
Then Create a Container using the Following command:-
```
sudo ctr container create docker.io/library/redis:latest redis
```
Get The List Of containers using the following command:-
```
sudo ctr container list
```
At last Delete, The Container using this command 
```
sudo ctr container delete redis
```
![4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648891584499/s8U3FNe_1.png)
Don't forget the Last Step Neither this could happen to you

![1648310249789.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648894381239/Zgi9sJgQC.jpg)





Complete Operation:-

![Screenshot_from_2022-02-17_22-42-05 (1).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648894876188/GcJZrOSKc.png)

Thanks for Stick with me. 