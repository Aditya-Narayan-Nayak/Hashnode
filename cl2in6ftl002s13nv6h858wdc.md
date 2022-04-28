## Getting Started with K6

#### Load Testing:-
Load testing is an effective way how your application is going to behave before it Goes to production.

### What is k6?
Grafana k6 is an open-source load testing tool that makes performance testing easy and productive for engineering teams.

### Installation:-
k6 has packages for Linux, Mac, and Windows. As alternatives, you can also use a Docker container or a prebuilt binary.

#### For ubuntu:-
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
echo "deb https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
sudo apt-get update
sudo apt-get install k6
```
#### For mac:-
```
brew install k6
```
#### For windows:-
```
winget install k6
```
Let's Get started by Running a Simple Script on a Local Machine:-

#### Step 1:-
Copy the code below, paste it into your favorite editor, and save it as script.js
```
import http from 'k6/http';
import { sleep } from 'k6';

export default function () {
  http.get('https://test.k6.io');
  sleep(1);
}
```
#### Step2:-
Then, run k6 with this command:
```
k6 run script.js
```

### Lets Add some More Virtual User :-
#### Step3:-
##### Run a load test with more than one virtual user and a longer duration:
```
k6 run --vus 10 --duration 30s script.js
```
#### Step4:-
##### There is another option Instead of typing --vus 10 and --duration 30s each time you run the script, you can also include the options in your JavaScript file:
```
import http from 'k6/http';
import { sleep } from 'k6';
export const options = {
  vus: 10,
  duration: '30s',
};
export default function () {
  http.get('http://test.k6.io');
  sleep(1);
}
```
#### Step5:-
And after that run the command 
```
k6 run script.js
```
#### Step6:-
#### Also, we can Increase and Decrease Virtual User Load By Using K6
To configure ramping, use the options. stages property.
```
import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  stages: [
    { duration: '30s', target: 20 },
    { duration: '1m30s', target: 10 },
    { duration: '20s', target: 0 },
  ],
};

export default function () {
  const res = http.get('https://httpbin.test.k6.io/');
  check(res, { 'status was 200': (r) => r.status == 200 });
  sleep(1);
}
```
#### K6 support test Execution in Diffrent Enviroments

- private/on-prem

- Cloud

- Cluster


#### Step7:-
Let's see how we can run K6 In a cloud Environment

To run cloud tests from the CLI:

- Register a k6 Cloud account.

- Log in to your account via the CLI.

- Use the k6 cloud command to run the script you already have.

```
k6 cloud script.js
```


#### Thanks a lot for reading this Blog. I wish you Enjoyed It. If you find it interesting please make sure Like it. If you have any queries get in touch with me on LinkedIn / Twitter, links are Down below.  Have a Nice day 😊 !

%[https://www.linkedin.com/in/aditya-narayan-nayak/]

%[https://twitter.com/AdityaN71677515]




