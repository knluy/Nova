

NAME: ubuntu-pro-1604-xenial-v20220810
PROJECT: ubuntu-os-pro-cloud
FAMILY: ubuntu-pro-1604-lts
DEPRECATED:
STATUS: READY

gcloud compute images create nested-ubuntu-focal --source-image-family=ubuntu-2004-lts --source-image-project=ubuntu-os-cloud --licenses https://www.googleapis.com/compute/v1/projects/vm-options/global/licenses/enable-vmx

Pro
gcloud compute instances create temp-image-base --image-family=projects/ubuntu-os-pro-cloud/global/images/family/ubuntu-pro-1604-lts --zone=asia-east1-b

minimal
gcloud compute instances create temp-image-base --image-family=projects/ubuntu-os-cloud/global/images/family/ubuntu-minimal-1604-lts --zone=asia-east1-b

stop instance
gcloud compute instances stop temp-image-base --zone=asia-east1-b

gcloud compute images create nested-vm-image --source-disk=temp-image-base --source-disk-zone=asia-east1-b --licenses https://www.googleapis.com/compute/v1/projects/vm-options/global/licenses/enable-vmx

gcloud compute instances create nested-vm --zone asia-east1-b --image=nested-vm-image --machine-type=n1-standard-4 --boot-disk-size=100GB