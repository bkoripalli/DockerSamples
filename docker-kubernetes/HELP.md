gcloud services enable compute.googleapis.com container.googleapis.com
gcloud services enable containerregistry.googleapis.com


Step1: Pull the code.


Step2: Build an image

ex: docker build -t gcr.io/$GOOGLE_CLOUD_PROJECT/date-app .

Step3: Push an image to gcr.io
ex:docker tag gcr.io/$GOOGLE_CLOUD_PROJECT/date-app
ex: docker push gcr.io/$GOOGLE_CLOUD_PROJECT/date-app

Step4: Create a cluster

ex: gcloud container clusters create date-app-cluster --num-nodes 2 --machine-type n1-standard-1 --zone us-central1-c

Step5: Create a deployment

kubectl create deployment first-deploy --image=gcr.io/$GOOGLE_CLOUD_PROJECT/date-app

Step6: Create a Service
ex:kubectl create service loadbalancer date-app --tcp=8080:8080