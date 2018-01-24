# Develop and Evaluate  Keras Deep Learning Models on AWS

Large ML/DL models require a lot of compute time to run. 
It can run them on your CPU that may take hours or days to get a result. 
If you have a GPU on your desktop, you can drastically speed up the training time of your deep learning models.

#### Guide get access to GPUs to speed up the training of your deep learning models by using the (AWS) 

### Step By Step Guide

- Setup Your AWS Account.
- Launch Your AWS Instance.
- Login and Run Your Code.
- Close Your AWS Instance.


## 1. Setup Your AWS Account
[Create account / Login](https://www.amazon.com/your-account) on Amazon Web Services.

1. Create an account by the [AWS portal](https://www.amazon.com/) and click `“Sign in to the Console”`. 
Then sign in Amazon account or create a new account

2. If you are creating a new account, then will need to provide a valid credit card that Amazon can charge later.
The process is a lot quicker if you have an Amazon account.
Note:Amazon do not charge on basic EC2 instance for a year.

Once you have an account you can log into the Amazon Web Services console.

## 2. Launch Your AWS Instance

 You want to launch an EC2 virtual server instance on which you can run Keras.

Launching an instance is as easy as selecting the image to load and starting the virtual server. Thankfully there is already an image available that has almost everything we need it is called the [Deep Learning AMI Amazon Linux](https://aws.amazon.com/machine-learning/amis/) Version and was created and is maintained by Amazon. Let’s launch it as an instance.

- 1. Login to your AWS console.
![AWS Console](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/aws-console.png)
- 2. Click on EC2 for launching a new virtual server.
- 3. Select “US West Orgeon” from the drop-down in the top right hand corner. Otherwise you will not be able to find the image we plan to use.
- 4. Click the `“Launch Instance”` button.
- 5. Click `“Community AMIs”`. An AMI is an Amazon Machine Image. It is a frozen instance of a server that you can select and instantiate on a new virtual server.
![Community AMIs](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Community-AMIs.png)

- 6. Enter `“ami-dfb13ebf”` (this is the current AMI id for v2.0 but the AMI may have been updated since, you check for a more recent id) in the “Search community AMIs” search box and press enter. You should be presented with a single result.
![Search for Deep Learning AMI](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Search-for-Deep-Learning-AMI-1024x266.png)

- 7. Click `“Select”` to choose the AMI in the search result.
- 8. Now you need to select the hardware on which to run the image. Scroll down and select the `“g2.2xlarge”` hardware. This includes a GPU that we can use to significantly increase the training speed of our models.
![Select g2.2xlarge Hardware](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Select-g2.2xlarge-Hardware.png)

- 9. Click “Review and Launch” to finalize the configuration of your server instance.
- 10. Click the “Launch” button.
- 11. Select Your Key Pair.
  -If you have a key pair because you have used EC2 before, select “Choose an existing key pair” and choose your key pair    from the list. Then check “I” acknowledge…”.
  -If you do not have a key pair, select the option “Create a new key pair” and enter a “Key pair name” such as keras-keypair. Click the “Download Key Pair” button.
![Select Your Key Pair](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Select-Your-Key-Pair.png)

- 12. Open a Terminal and change directory to where you downloaded your key pair.
- 13. If you have not already done so, restrict the access permissions on your key pair file. This is requred as part of the SSH access to your server. For example:

    cd Downloads
    chmod 600 keras-aws-keypair.pem

- 14. Click “Launch Instances”. If this is your first time using AWS, Amazon may have to validate your request and this could take up to 2 hours (often just a few minutes).
- 15. Click “View Instances” to review the status of your instance.
![Deep Learning AMI Status](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Deep-Learning-AMI-Status.png)

Your server is now running and ready for you to log in.


## 3. Login, Configure and Run
Now log in and start using that server instance you have launched.

- 1. Click `View Instances` in your Amazon EC2 console if you have not already.
- 2. Copy `Public IP` (down the bottom of the screen in Description) to clipboard. In this example my IP address is `54.111.77.77.` **Do not use this IP address**, your IP address will be different.
- 3. Open a Terminal and change directory to where you downloaded your key pair. Login to your server using SSH, for example:

`ssh -i keras-aws-keypair.pem ec2-user@54.111.77.77`
- 4. When prompted, type “yes” and press enter.
You are now logged into your server.
![Terminal Login to Deep Learning AMI](https://github.com/PakistanAI/ComputeEasy/blob/master/Keras%20Deep%20Learning%20Models%20on%20AWS/images/Terminal-Login-to-Deep-Learning-AMI.png)

We may need to make two small changes before we can start using Keras. If the AMI has been updated since writing this, you may not need to make these changes

This will just take a minute. You will have to do these changes each time you start the instance.

### 3a. Update Keras

Update to a specific version of Keras known to work on this configuration, at the time of writing the latest version of Keras is version 2.0.2 We can specify this version as part of the upgrade of Keras via pip.


`sudo pip install --upgrade keras==2.0.2`

You can also confirm that Keras is installed and is working correctly by typing:


`python -c "import keras; print keras.__version__"`

You should see:

    Using TensorFlow backend.
    I tensorflow/stream_executor/dso_loader.cc:135] successfully opened CUDA library libcurand.so.7.5 locally
    ...
    ...
    2.0.2
You are now free to copy-and-paste or upload your Keras python scripts to the server and start running them.

You may also want to install scikit-learn:

`sudo pip install scikit-learn`

Try something new on your new instance, see this tutorial:

[Keras Tutorial: The Ultimate Beginner’s Guide to Deep Learning in Python
](https://elitedatascience.com/keras-tutorial-deep-learning-in-python)
## 4. Close Your AWS Instance
When you are finished with your work you must close your instance.

Remember you are charged by the amount of time that you use the instance. you do not want to leave an instance on if you are not using it.

- 1. Log out of your instance at the terminal, for example you can type: `exit`
- 2. Log in to your AWS account with your web browser.
- 3. Click EC2.
- 4. Click “Instances” from the left-hand side menu.
![Review Your List of Running Instances](/images/logo.png)

- 5. Select your running instance from the list (it may already be selected if you only have one running instance).
Select Your Running AWS Instance
![Select Your Running AWS Instance](/images/logo.png)

- 6. Click the “Actions” button and select “Instance State” and choose “Terminate”. Confirm that you want to terminate your running instance.
It may take a number of seconds for the instance to close and to be removed from your list of instances.

## More Resources For Deep Learning on AWS

[Deep Learning AMI with Source Code](https://aws.amazon.com/marketplace/pp/B01M0AXXQB)

[10 Command Line Recipes for Deep Learning on AWS](https://machinelearningmastery.com/command-line-recipes-deep-learning-amazon-web-services/)
