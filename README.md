# Potato Disease Prediction

Early blight and late blight are the most common diseases on potato. They usually take huge losses to farmers. Although the names of the two diseases are the only one-word difference, some growers do not know exactly about the difference between early blight and late blight.

* Early Blight - Symptoms of early disease first appear in the base of the affected plant, with roughly round brown spots on the leaves and stems.
* Late blight  - The most obvious early signs of late blight are brown spots or disease spots on plant stems.
![images](https://user-images.githubusercontent.com/42634704/136694359-5722e1c6-31d2-4d44-b335-4434e4a37a8e.JPG)


## Techincal Aspect:

 ![workflow](https://user-images.githubusercontent.com/42634704/136700449-fd8630f9-448a-4ede-96b4-d98d615238ee.jpg)

## Dataset:
1. Download the data from [kaggle](https://www.kaggle.com/arjuntejaswi/plant-village), and only keep folders related to Potatoes.

## Setup for Python:
1. Install Python ([Setup Instructions](https://wiki.python.org/moin/BeginnersGuide)) 
2. Install Python Packages for the Project

        pip3 install -r training/requirements.txt
        pip3 install -r api/requirements.txt
        
## Setup for ReactJS
1. Install Nodejs ([Setup instructions](https://nodejs.org/en/download/package-manager/))
2. Install NPM ([Setup instructions](https://nodejs.org/en/download/package-manager/))
3. Install dependencies

        cd frontend
        npm install --from-lock-json
        npm audit fix
4. Copy  `.env.example` as `.env` 
5. Change API url in `.env`
      
      
 ## Running the API

### Using FastAPI

1. Get inside `api` folder

```bash
cd api
```

2. Run the FastAPI Server using uvicorn

```bash
uvicorn main:app --reload --host 0.0.0.0
```

3. Your API is now running at `0.0.0.0:8000`    
     
      
## Running the Frontend

1. Get inside `api` folder

```bash
cd frontend
```

2. Copy the `.env.example` as `.env` and update `REACT_APP_API_URL` to API URL if needed.
3. Run the frontend

```bash
npm run start
```      
      
## Deploying the TF Model on Google Cloud

1. Create a [GCP account](https://console.cloud.google.com/freetrial/signup/tos?_ga=2.25841725.1677013893.1627213171-706917375.1627193643&_gac=1.124122488.1627227734.Cj0KCQjwl_SHBhCQARIsAFIFRVVUZFV7wUg-DVxSlsnlIwSGWxib-owC-s9k6rjWVaF4y7kp1aUv5eQaAj2kEALw_wcB).
2. Create a [Project on GCP](https://cloud.google.com/appengine/docs/standard/nodejs/building-app/creating-project) (Keep note of the project id).
3. Create a [GCP bucket](https://console.cloud.google.com/storage/browser/).
4. Upload the potatoes.h5 model in the bucket in the path `models/potatos.h5`.
5. Install Google Cloud SDK ([Setup instructions](https://cloud.google.com/sdk/docs/quickstarts)).
6. Authenticate with Google Cloud SDK.

```bash
gcloud auth login
```

7. Run the deployment script.

```bash
cd gcp
gcloud functions deploy predict_lite --runtime python38 --trigger-http --memory 512 --project project_id
```

8. Your model is now deployed.
9. Use Postman to test the GCF using the [Trigger URL](https://cloud.google.com/functions/docs/calling/http).

GoogleCloud : https://cloud.google.com/blog/products/ai-machine-learning/how-to-serve-deep-learning-models-using-tensorflow-2-0-with-cloud-functions


## Inspiration :
https://youtube.com/playlist?list=PLeo1K3hjS3ut49PskOfLnE6WUoOp_2lsD 

