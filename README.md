# xbee-socket

Socket client for https://code.google.com/p/xbee-api/. While xbee-api requires a dedicated serial connection to the radio, this uses a socket connection to https://github.com/andrewrapp/xbee-serial-server to send and receive packets. This allows several applications to share the same radio (coordinator).
  
  Example: Connect to xbee-serial-server on host pi, port 9000 and send the AI AT commmand

```java  
XBee xbee = new XBee(new XBeeConfiguration().withStartupChecks(false));
// connect to xbee-serial-server on host "pi" with port 9000
xbee.initProviderConnection((XBeeConnection)new SocketXBeeConnection("pi", 9000));
AtCommandResponse response = (AtCommandResponse) xbee.sendSynchronous(new AtCommand("AI"));
System.out.println("Received AI response " + response);
xbee.close();
```
