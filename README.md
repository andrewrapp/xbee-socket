# xbee-socket

Socket client for xbee-api. While xbee-api requires a dedicated serial connection to the radio, this allows many application to share the same radio. Requires xbee-serial-server
  
  Example: Connect to xbee-serial-server on host pi, port 9000 and send the AI AT commmand
  
XBee xbee = new XBee(new XBeeConfiguration().withStartupChecks(false));
xbee.initProviderConnection((XBeeConnection)new SocketXBeeConnection("pi", 9000));
AtCommandResponse response = (AtCommandResponse) xbee.sendSynchronous(new AtCommand("AI"));
System.out.println("Received AI response " + response);
xbee.close();
