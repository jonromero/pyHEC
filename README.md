I couldn't find an official and simple Python SDK for sending data to Splunk's HTTP Event Collector (HEC), so this is it. One simple file, two lines of code.

Feel free to fork and play around.

Install it:

    > virtualenv /tmp/hec
    > source /tmp/hec/bin/activate
    > pip install -r requirements.txt

Use it:
    
    # import pyHEC
    from pyHEC import PyHEC

    # use your token (read how to get it here: http://blogs.splunk.com/2015/09/22/turbo-charging-modular-inputs-with-the-hec-http-event-collector-input/)
    hec = PyHEC("PUT_YOUR_TOKEN_HERE", "http://localhost")
    
    # this is the event you want to send    
    event = {"text":"this is a message in a bottle", "whatever_else":"blabla"}

    # you can select index, host, etc
    metadata = {"index":"default", "host":"jonromero"}

    # send the event with the metadata
    print hec.send(event, metadata)

    # or without metadata
    print hec.send(event)
    


This is not an official Splunk release.

Ping me [@jonromero](http://twitter.com/jonromero) if you need anything.