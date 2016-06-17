# GoogleTextToSpeech
Google Speech API Transcriber

	Transcribes a stereo 8k or 16k wav file via the google alpha speech API. 
	Prints results broken down by channel with  speech segment timestamps. 
    
Operation:

	The stereo file is inspected, then split into independent channels in memory, then auditok tokenizes each channel based on 
	values lower than a given threshold indicating silence. Each segment is sent to google (preferably in parallel when 
	their limits are better), and the responses are collected and sorted according to the time in which they occurred. 
    
	It is not safe to adjust the thread count, yet, due to the very low limits set by Google of 0.2 requests per second.

	Returns results broken down by channel with  speech segment timestamps. 

Requires:

	auditok
	gevent
	oauth2client
	google-api-python-client
 	googleapis-common-protos

Note:

	if speech_service_account.json and speech-discovery_google_rest_v1.json are in the current directory when this script
	is executed, the -a and -d flags don't need to be specified. 

Examples:

	python transcribe.py -f audio.wav      -> Get results for both channels
	python transcribe.py -f audio.wav -c A -> Get results just for the left channel
	python transcribe.py -f audio.wav -c B -> Get results just for the right channel



### Set Up to Authenticate With Your Project's Credentials

The example uses a service account for OAuth2 authentication.
So next, set up to authenticate with the Speech API using your project's
service account credentials.

Visit the [Cloud Console](https://console.cloud.google.com), and navigate to:
`API Manager > Credentials > Create credentials >
Service account key > New service account`.
Create a new service account, and download the json credentials file.

Then, set
the `GOOGLE_APPLICATION_CREDENTIALS` environment variable to point to your
downloaded service account credentials before running this example:

    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/your/credentials-key.json

If you do not do this, the REST api will return a 403. The streaming sample will
just sort of hang silently.

See the
[Cloud Platform Auth Guide](https://cloud.google.com/docs/authentication#developer_workflow)
for more information.
