# web-classifier-cats-dogs

NN hosted as service using Flask and JS

This simple classifier uses transfer learning to train an existing VGG16 model and by changing the last layer we create a new model which predicts if the uploaded image is _cat_ or _dog_

![cat](/cat.png)

![dog](/dog.png)

Note : The actual model is more than 500 MB so , have not hosted it on Github

After placing the model in repective directory start the Flask server using

- export FLASK_APP=predict_app.py
- flask run --host=0.0.0.0

Change the IP address to point to your webserver

To get predicitons from shell instead of browser

```console
$fileName='cat.png'        
$bytes = [IO.File]::ReadAllBytes($fileName)
$base64Image = [Convert]::ToBase64String($bytes)
$message = @{ image = $base64Image }
$jsonified = ConvertTo-Json $message
$response = Invoke-RestMethod -Method Post -Url "http://0.0.0.4:5000/predict" -Body $jsonified
$response.prediction | format-list
```

Credits : This was build using tutorials from this [DeepLizard Course](https://deeplizard.com/learn/playlist/PLZbbT5o_s2xrwRnXk_yCPtnqqo4_u2YGL)
