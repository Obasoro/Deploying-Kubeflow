# Tutorial: Building Your First Kubeflow Pipelines Workflow


This tutorial was carried on Debian/Linux system on Google Cloud Platform -ssh into my local system

The following API was deployed 

VM created, with 8vCPU, and 50G memory.

`$ gcloud compute disks create kfdisk --size 50G --image-project ubuntu-os-cloud --image-family ubuntu-minimal-1804-lts --zone us-central1-b`

<img width="406" alt="1" src="https://user-images.githubusercontent.com/29310552/158913143-661f2455-6ee4-49f0-b939-cd461c584324.PNG">

# Step 2: Step 2: Create an image with a license key required for nested virtualization.

`$ gcloud compute images create kfimage \
  --source-disk kfdisk --source-disk-zone us-central1-b \
  --licenses "https://compute.googleapis.com/compute/v1/projects/vm-options/global/licenses/enable-vmx"`
  
# Step 3: Create a GCE instance that uses the custom image we created.

`$ gcloud compute instances create kf-demo-vm --zone us-central1-b \
              --min-cpu-platform "Intel Haswell" \
              --image kfimage`


To access VM on your local machine using ssh, check the following commands on from this link

[Gcloud](https://cloud.google.com/compute/docs/connect/create-ssh-keys)

[Gcloud](https://cloud.google.com/compute/docs/instances/connecting-advanced)

<img width="447" alt="4" src="https://user-images.githubusercontent.com/29310552/158918269-f65eefe3-aa1e-414a-b371-bc0a0bb1067e.PNG">

# Step 4: Verify that nested virtualization is enabled on your image

`$ $ grep -cw vmx /proc/cpuinfo`

<img width="413" alt="5" src="https://user-images.githubusercontent.com/29310552/158918294-81bb304f-4384-4219-8fae-6b00b5425c5e.PNG">

Since you are in your local machine, having connected through SSH, run this commands;

`$ gsutil cp gs://manceps-public/lab-scripts/kf-install.sh .`

`$ chmod +x kf-install.sh`

`$ ./kf-install`







