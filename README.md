# PowerCloud-Cost-Efficient-EC2-Automation-with-Lambda-Triggers
Created an automated cost-optimization system that uses AWS Lambda and CloudWatch Events to schedule EC2 start/stop actions. Designed the solution to cut unnecessary runtime and lower cloud costs. Showcased skills in serverless automation



# Automated EC2 Start/Stop Using AWS Lambda & EventBridge

## Steps

### 1. Create EC2 Instances
### 2. Create IAM Roles for Lambda with EC2 Instance Accessibility
### 3. Create Lambda function to start and stop the EC2 Instances
### 4. Create Event Bridge Scheduler



Understood.
I will **correct only grammar, spelling, and formatting issues**.
I will **NOT change your steps, meaning, flow, or add/remove anything.**

Here is the corrected version:

---

````markdown
# Automate EC2 Start/Stop Using AWS Lambda & EventBridge

## Steps

### **1. Create and Start Two EC2 Instances**
- Instance name: **Powerproject1**
- Instance name: **Powerproject2**
- Start both instances and note the Instance IDs.

---

### **2. Create IAM Role**
- Go to IAM → Roles → Create Role
- Use case: **Lambda**
- Add permission policy: **EC2FullAccess**
- Role name: **myec2fullaccess**

---

### **3. Create Lambda Function**
- Create function name: **automate_power_cloud**
- Runtime: **Python 3.12**
- Execution role: **Existing role**
- Existing role: **myec2fullaccess**

---

### **3.1 Stop Instances Lambda Code**
- Open:  
  **https://repost.aws/knowledge-center/start-stop-lambda-eventbridge**
- Copy the code to stop the instances:

```python
import boto3  
region = 'us-west-1'
instances = ['i-12345cb6de4f78g9h', 'i-08ce9b2d7eccf6d26']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=instances)
    print('stopped your instances: ' + str(instances))
````

* Paste it into the Lambda code source.
* Change the instance IDs and region.
* Click **Deploy** and test.

**Test configuration:**

* Event name: **powercloudtext1**
* Save and Test.

---

### **3.2 Start Instances Lambda Code**

* Open:
  **[https://repost.aws/knowledge-center/start-stop-lambda-eventbridge](https://repost.aws/knowledge-center/start-stop-lambda-eventbridge)**
* Copy the code to start the instances:

```python
import boto3  
region = 'us-west-1'
instances = ['i-12345cb6de4f78g9h', 'i-08ce9b2d7eccf6d26']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=instances)
    print('started your instances: ' + str(event))
```

* Paste it into the Lambda code source.
* Change the instance IDs and region.
* Click **Deploy** and test.

**Test configuration:**

* Event name: **powercloudtext2**
* Copy region and instances and paste into JSON:

```json
{
  "region": "us-west-1",
  "instances": ["i-12345cb6de4f78g9h", "i-08ce9b2d7eccf6d26"]
}
```

* Save and Test.

```

---

 
