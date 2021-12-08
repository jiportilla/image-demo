<h1 align="center" style="border-bottom: none;">🔎 Image Demo </h1>

<h3> Localize and identify multiple objects in a single image.</h3>

Source:

[https://developer.ibm.com/exchanges/models/all/max-object-detector/](https://developer.ibm.com/exchanges/models/all/max-object-detector/)



### Flow

This model recognizes the objects present in an image from the 80 different high-level classes of objects in the COCO Dataset. The model consists of a deep convolutional net base model for image feature extraction, together with additional convolutional layers specialized for the task of object detection, that was trained on the COCO data set. The input to the model is an image, and the output is a list of estimated class probabilities for the objects detected in the image. The model is based on the SSD Mobilenet V1 object detection model for TensorFlow.



Enjoy the demo!

<h3>BADM-4830</h3>
</p>

1. login to the development virtual machine VM hosted on AWS cloud

	 `
    ssh ubuntu@XX.XXX.XXX.XXX
    `
    
    *Make sure to post your **ssh public key** to the Watson studio project used for this lesson
    
2. Navigate to class subdirectory

	`cd /home/ubuntu/4830`
3. Create & navigate to your own directory

	`mkdir userName`
	
	`cd userName`
	
	For example:
	
	`mkdir ivanp`
	
	`cd ivanp`
	
	
4. Clone Module 7 repository from github

	`git clone https://github.com/jiportilla/image-demo.git`
	
5. Change directory to the module 7 directory

	`cd image-demo/`
6. Test your `docker` installation by running the following command:

	`docker run hello-world`
	
	You will see:
	
	```
	Hello from Docker.
	This message shows that your installation appears to be working correctly.
```


### Object Detection


7. This model can be deployed using the following mechanisms:


Deploy from Dockerhub:

```
docker run -it -p 5000:5000 codait/max-object-detector
```
	
You will see:
	
```
 ...
 * Serving Flask app "MAX Object Detector" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
  Use a production WSGI server instead.
 * Debug mode: off
 * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://172.17.0.2:5000/ (Press CTRL+C to quit)
```

### Example usage

1. Open another terminal window, login to the same VM and test with cURL


###Test the model using cURL

Once deployed, you can test the model from the command line. For example:


```
curl -F "image=@images/dog.jpg" -XPOST http://127.0.0.1:5000/model/predict | jq

```

You will see:

```
{
  "status": "ok",
  "predictions": [
    {
      "label_id": "18",
      "label": "dog",
      "probability": 0.9205932021141052,
      "detection_box": [
        0.06259137392044067,
        0.4081900417804718,
        0.9334007501602173,
        0.7712860107421875
      ]
    }
  ]
}
```
