# Console application based on Shapes which displays use of late joining instances

Skeleton created via
 
```bash
rtiddsgen -language C++11 -platform x64Linux4gcc7.3.0 -example x64Linux4gcc7.3.0 -create makefiles -create typefiles -d c++11 shapes.idl
```

The QoS is configure to use TRANSIENT_LOCAL durability with an AUTO_WRITER_DEPTH. 
The history QoS is set to KEEP_LAST_HISTORY_QOS with a depth of 50

The publisher writes a shapes sample every second with a random number between 1 and 10 in the shapesize field. 
It keeps track of the last "history depth" count of these random numbers and every time a sample is written, prints the sample count, value and the sum of all the values.

The subscriber reads the history depth from the reader's QoS and every time it reads a sample, updates a local sum of the last "history depth" count of the values in the shapesize field. Every time an unread sample is received, the subscriber prints the received count, value of the last sample and the sum of the last "history depth" count of values.

Starting subscriber instances after the publish has started, should see the subscriber read up to all the "history depth" samples,
and start displaying the same terminal outputs (counts and sums) as the publisher/other subscribers
