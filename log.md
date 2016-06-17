#6/17/2016

Changed the connection to the speech service in transcribe.py.

Audio needs to be in correct format, sln16:

sox test_recording.wav -t raw -r 16000 -c 1 test_recording.sln16

 python transcribe.py -f test_recording.flac -a notefree-20eeaca71278.json


Can't get correct audio format to work. Not sure why.

