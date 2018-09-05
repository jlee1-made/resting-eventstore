# Debugging [Event Store](https://geteventstore.com/)

This `Dockerfile` provides an Event Store configured to use heartbeat timeouts set to high values.

This is useful if you want to use a debugger to step through code that talks to Event Store using the Event Store TCP API -- such as code that uses [photon-pump](https://github.com/madedotcom/photon-pump).  Event Store's TCP API makes use of a 'heartbeat' to ensure that unused connections are not left open.  This means that if you're sitting at a debugger prompt (e.g. at a pdb prompt) -- and therefore not running your event loop for tens of seconds at a time -- you'll find that you get disconnected from Event Store.

To build and run:

    docker build -t resting-eventstore .
    docker run -d resting-eventstore
