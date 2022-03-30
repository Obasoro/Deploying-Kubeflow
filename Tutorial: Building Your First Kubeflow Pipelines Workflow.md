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

# Another Option

# Used `minikf` to deploy and launch kubeflow

1. Go to the Marketplace and search for minikf.

2. Enable and deploy. It would take few minute to iniatialize. Keep the user name and password for the kubeflow. SSH into the minikf and type `minikf` to initialize kubeflow

<img width="812" alt="ssh" src="https://user-images.githubusercontent.com/29310552/160821399-7e7e04aa-2a36-4e13-bac7-4c852a870be7.PNG">


<img width="952" alt="Capture" src="https://user-images.githubusercontent.com/29310552/160817691-d9b15803-4a05-4d00-b8be-915f8a2460b1.PNG">

<img width="947" alt="Capture2" src="https://user-images.githubusercontent.com/29310552/160818702-089103a8-3fd7-4187-b29a-2620ceef8dca.PNG">

3. Click Notebook to initilaize ther server

<img width="763" alt="Capture3" src="https://user-images.githubusercontent.com/29310552/160820962-4ab2df3b-cf48-4b5e-b1af-d9a41f384ddb.PNG">

4. click connect and the server would be up and running

5. Click terminal and `git clone https://github.com/manceps/manceps-canonical.git`

6. Open the "KF_Fashion_MNIST.ipynb" file

<img width="719" alt="file" src="https://user-images.githubusercontent.com/29310552/160822360-0e297357-706d-4878-ae12-58a56f3c006e.PNG">

# The MNIST notebook cells.

1.<img width="738" alt="note1" src="https://user-images.githubusercontent.com/29310552/160823325-193c8f6f-cbb1-402e-8dca-8c99cc61e9d1.PNG">

<img width="723" alt="note2" src="https://user-images.githubusercontent.com/29310552/160823519-fe628b83-00f4-4893-8922-2acd29f32944.PNG">

Data exploration been carried out

<img width="749" alt="note3" src="https://user-images.githubusercontent.com/29310552/160823889-8ee0354b-5b6f-402c-9138-fb8bfed7ba06.PNG">

Image preprocessing 

<img width="726" alt="note4" src="https://user-images.githubusercontent.com/29310552/160824150-0a2fe32a-1d3f-4edd-b560-1c8b338186d7.PNG">

Deploy KFT using the code

<img width="637" alt="deploy kft" src="https://user-images.githubusercontent.com/29310552/160831336-63c06382-c50f-4f6b-b0a2-aa5480ef4198.PNG">

build kubeflow pipeline

<img width="717" alt="client" src="https://user-images.githubusercontent.com/29310552/160831713-97a0022e-09e4-4b2b-a357-44e1ee827e53.PNG">




















