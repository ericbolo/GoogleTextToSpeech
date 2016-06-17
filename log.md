#6/17/2016

Changed the connection to the speech service in transcribe.py.

Audio needs to be in correct format, sln16:

sox test_recording.wav -t raw -r 16000 -c 1 test_recording.sln16

 python transcribe.py -f test_recording.flac -a notefree-20eeaca71278.json


Can't get correct audio format to work. Not sure why.
Trying to convert to linear16 with ffmpeg. Apt-get ffmpeg installation failed so following instructions at https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

https://delog.wordpress.com/2011/11/04/convert-wav-to-pcm-using-ffmpeg/

http://www.audioexpert.com/register.php, ericbolo, CaoeChloe123 (or thehumbling123)

Latest test: python transcribe.py -f again.wav -a notefree-20eeaca71278.json