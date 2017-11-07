# <1> Assign the your API keys
Get your free Subscription key [here](https://azure.microsoft.com/en-us/try/cognitive-services/)

Click Emotion API's [Get API key]

Check agree & accept buttom and select country [Korea]

login using your preferred account

so you assign the your APIs keys

---
# <2> Write the code

Make a python file
```python
########### Python 3.2 #############
import http.client, urllib.request, urllib.parse, urllib.error, base64, sys

headers = {
    # Request headers. Replace the placeholder key below with your subscription key.
    'Content-Type': 'application/json',
    'Ocp-Apim-Subscription-Key': '13hc77781f7e4b19b5fcdd72a8df7156',
}

params = urllib.parse.urlencode({
})

# Replace the example URL below with the URL of the image you want to analyze.
body = "{ 'url': 'http://example.com/picture.jpg' }"

try:
    # NOTE: You must use the same region in your REST call as you used to obtain your subscription keys.
    #   For example, if you obtained your subscription keys from westcentralus, replace "westus" in the 
    #   URL below with "westcentralus".
    conn = http.client.HTTPSConnection('westus.api.cognitive.microsoft.com')
    conn.request("POST", "/emotion/v1.0/recognize?%s" % params, body, headers)
    response = conn.getresponse()
    data = response.read()
    print(data)
    conn.close()
except Exception as e:
    print(e.args)
####################################
```


source the [here](https://docs.microsoft.com/en-us/azure/cognitive-services/emotion/quickstarts/python)
