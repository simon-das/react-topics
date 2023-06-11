# Websocket
WebSocket is a communication protocol that provides full-duplex communication channels over a single TCP connection. It enables real-time, bidirectional communication between a client (such as a web browser) and a server.

WebSockets are commonly used in applications that require real-time updates, such as chat applications, collaborative editors, and real-time data visualization.

In React, you can utilize WebSocket for implementing real-time features in your applications. Here's a basic example of using WebSocket in React:

<br>

```javascript
import React, { useEffect, useState } from 'react';

const WebSocketExample = () => {
  const [message, setMessage] = useState('');
  const [ws, setWebSocket] = useState(null);

  useEffect(() => {
    // Create a new WebSocket connection
    const socket = new WebSocket('wss://example.com/ws');

    // Set up event handlers for WebSocket events
    socket.onopen = () => {
      console.log('WebSocket connection established');
    };

    socket.onmessage = (event) => {
      const receivedMessage = event.data;
      setMessage(receivedMessage);
    };

    socket.onclose = () => {
      console.log('WebSocket connection closed');
    };

    // Save the WebSocket instance in state
    setWebSocket(socket);

    // Clean up the WebSocket connection on component unmount
    return () => {
      socket.close();
    };
  }, []);

  const sendMessage = () => {
    if (ws && ws.readyState === WebSocket.OPEN) {
      ws.send('Hello, server!');
    }
  };

  return (
    <div>
      <p>Received message: {message}</p>
      <button onClick={sendMessage}>Send Message</button>
    </div>
  );
};

export default WebSocketExample;
```

<br>

Note that you should replace `'wss://example.com/ws'` with the actual WebSocket server URL you want to connect to.
