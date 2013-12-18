Android SpeechRecognizer plugin for Cordova/Phonegap
===================================
This plugin provides access to the speech recognition feature. This plugin will recognize commands, phrases, etc as spoken by the user.

![Screenshot speak now](/screenshots/speaknow.png "Speak now")

Requirements
-------------
Above Android 2.2 and best work in above 4.0
Compatible with Cordova 3.0.

Support
---------------------
For free community support, please use the issue tracker.  
To get professional non-free support for the plugin, please contact me at gcharhon(at)smartmobilesoftware.com.



### Automatically (CLI / Plugman)
SpeechRecognizer is compatible with [Cordova Plugman](https://github.com/apache/cordova-plugman), compatible with [PhoneGap 3.0 CLI](http://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html#The%20Command-line%20Interface_add_features), here's how it works with the CLI:

```
$ phonegap local plugin add https://github.com/mayurloved/speechrecognizer.git
```
or
```
$ cordova plugin add https://github.com/mayurloved/speechrecognizer.git
```

===> then include SpeechRecognizer.js file from www\plugins\com.phonegap.plugins.speech

===> copy below html code in your html and Done


----------------------------------------------- 
If your want to include plugin manually then also you can include it.

step 1 : LanguageDetailsChecker.java,SpeechRecognizer.java file in this package  com.phonegap.plugins.speech

step 2 : add plugin in xml file
for >3.0 or
```	
	 <feature name="SpeechRecognizer">
        <param name="android-package" value="com.phonegap.plugins.speech.SpeechRecognizer" />
    </feature>
```
	for <2.9 
```
	   <plugin name="SpeechRecognizer" value="com.phonegap.plugins.speech.SpeechRecognizer"/>
```
step 3 : copy SpeechRecognizer.js file in your www folder and include in .html file 

	<script type="text/javascript" src="SpeechRecognizer.js"></script>
``` 
step 4 : include or copy or use below index.html file and check application.

 	
* Create a 'com/phonegap/plugins/speech' folder under 'src' and add [LanguageDetailsChecker.java](LanguageDetailsChecker.java) and [SpeechRecognizer.java](SpeechRecognizer.java) to it.
* Add [SpeechRecognizer.js](SpeechRecognizer.js) in your www folder.  
* Add in your index.html  
`<script type="text/javascript" charset="utf-8" src="SpeechRecognizer.js"></script>`  
* In res/xml/config.xml, add 

```xml
<feature name="SpeechRecognizer">  
      <param name="android-package" value="com.phonegap.plugins.speech.SpeechRecognizer"/>  
</feature> 
```    

Usage
-------

#### Start recognition
Show the recognition dialog and get the recognized sentences

    SpeechRecognizer.startRecognize(success, error, maxMatches, promptString, language);
parameters
* success : The success callback. It provides a json array with all possible matches. Example: "[hello world,low world,hello walls]".
* error : The error callback.
* maxMaches : Maximum of returned possibles sentences matches.
* promptString : String shown below the Google logo and the microphone icon. Instruct the user of what to. Example: "Speak now"
* language : Language used by the speech recognition engine. Example: "en-US".

#### Supported languages
Get the list of supported languages codes

    SpeechRecognizer.getSupportedLanguages(success, error);
parameters
* success : The success callback. It provides a json array of all the recognized language codes. Example: "[en-US,fr-FR,de-DE]".
* error : The error callback.

Full example
----------------
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Speech Recognition plugin demo</title>
        <script type="text/javascript" src="cordova-2.8.js"></script>
        <script type="text/javascript" src="SpeechRecognizer.js"></script>
    </head>
    <body>

        <script type="text/javascript">

            function onDeviceReady(){
                console.log("Device is ready");
            }

            function recognizeSpeech() {
                var maxMatches = 5;
                var promptString = "Speak now";	// optional
                var language = "en-US";						// optional
                window.plugins.speechrecognizer.startRecognize(function(result){
                    alert(result);
                }, function(errorMessage){
                    console.log("Error message: " + errorMessage);
                }, maxMatches, promptString, language);
            }

            // Show the list of the supported languages
            function getSupportedLanguages() {
                window.plugins.speechrecognizer.getSupportedLanguages(function(languages){
                    // display the json array
                    alert(languages);
                }, function(error){
                    alert("Could not retrieve the supported languages : " + error);
                });
            }

            document.addEventListener("deviceready", onDeviceReady, true);
        </script>

        <button onclick="recognizeSpeech();">Start recognition</button>
        <button onclick="getSupportedLanguages();">Get Supported Languages</button>
    </body>
</html>
```

License
----------------

Copyright (c) 2011-2013  
Mayur Panchal (https://github.com/mayurloved/)  

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

[![Mayur Panchal](http://excellentwebworld.com/wp-content/uploads/2013/07/logo.png)](http://www.excellentwebworld.com/ "Blogging")