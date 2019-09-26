 
# MIT 6.884 Google Cloud Account Initialization
  
Deep learning requires lots of computational resources, so for this class we introduce the Google Cloud Platform to run and store your models for your convenience. You will each be provided with a coupon for $50, which roughly translates to 5 hours of compute time/week. You will use the same account for the entire semester - including the final project - so don’t spend it all in one place! You will run the code in this notebook using Google Cloud Datalab. For this problem set, you will be initializing a GPU-enabled Cloud DataLab instance.  
  
**>> Once you have completed Datalab setup in this README, please download the "[DOWNLOAD & UPLOAD TO DATALAB]" file in this repo and run it in your newly created Datalab environment to begin!<<** 
  
<br/><br/>
### Getting Started: First time using Google Cloud / Datalab:
Redeem your Google Cloud education grant with the coupon emailed to you before class. Use your own gmail account to log in to the Google Cloud console.  
  
Create a GCP project, enable billing and APIs following instructions [here](https://cloud.google.com/datalab/docs/quickstart#before-you-begin).  
Install and initialize the Cloud SKD following instructions [here](https://cloud.google.com/sdk/docs/). You only need to initialize it once by running (the login window will pop up in your browser, log in using your gmail account and complete the rest of the steps from your command line as prompted):  
  
```
gcloud init
```

NOTE: **Compute Region**. You may be asked to select a region in this step. We recommend `"us-east1-d"`, which has support for GPU-enabled machines.

  
For Windows users, add the full path to `google-cloud-sdk\bin` into your `PATH` variable before using datalab command.  
  
 
<br/><br/>
### Set up and launch Cloud Datalab  
Following instructions here. Install datalab with gcloud:  
  
```
gcloud components update
gcloud components install datalab
```

Then create a datalab instance. If you expeerience **GPU QUOTA** OR **REGION** errors, please see the notes below! 
  
```
datalab beta create-gpu [YOUR INSTANCE NAME HERE] #when asked to select a region, choose us-east-d
```

Once the above code has run, it will initialize the instance and establish an SSH access automatically for you. Once prompted, point your web browser at http://localhost:8081 to start using datalab. If everything worked correctly, your browser will open to a view of the cloud datalab console.  
  
NOTE: **GPU REGIONS**  
Only a subset of google cloud zones support GPU instances. You can find the list [here](https://cloud.google.com/compute/docs/gpus/). We recommend launching in *zone 3* (us-east1-d) which supports GPU instances. 

NOTE: **GPU REGIONS**  
If this is your first time using GPU-enabled computing on Google Cloud, you may need to add a GPU to your Google Compute engine quotas. You can do this at the [Google Cloud Quotas page](https://console.cloud.google.com/iam-admin/quotas?_ga=2.264175503.-20908204.1567002379&_gac=1.229247598.1569293037.CjwKCAjw2qHsBRAGEiwAMbPoDN5P1DcjngZwAd-x074wHVFtCMGC8q_q5QXgHd34S1V3hLInf8LJNBoCkKkQAvD_BwE). You will need to request an increase of "Current Limit" to "1" of the `GPUs All Regions` quota. 


Note: **OTHER GPU ISSUES (GPU-less Datalab)**  
If after following the above, you are still having issues running a GPU-enabled cloud compute instances, For those users or , you can still create a GPU-less datalab instance with the command:  

```
datalab create [...]
``` 
<br/>
in place of `datalab beta create [...]`. You will also need to comment any calls to `model.cuda()` in the Jupyter notebook, as noted in the Jupyter notebook code. Good luck!

<br/><br/>
### Pricing
There is no charge for using Google Cloud Datalab. However, you do pay for any Google Cloud Platform resources you use with Cloud Datalab (compute and storage resources, etc.). E.g. you incur costs from the time of creation to the time of deletion of the Cloud Datalab VM instance. Keep in mind that you only have limited budget with $125 coupon so don’t let your instance run forever!

<br/><br/>
### Stopping an instance
Run the following command to stop your Cloud Datalab instance to avoid incurring unnecessary costs when you want to pause using Cloud Datalab

```
datalab stop instance-name
```

When you are ready to start using Cloud Datalab again (or if your terminal command window is closed or interrupted while running datalab and you want to reconnect), run datalab connect instance-name command to restart the instance. You can also stop, restart, and manage your VM instances in the Google Compute Engine any time.
