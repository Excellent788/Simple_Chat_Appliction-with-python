# Simple Chat Application

This is a simple chat application implemented using Python's socket library. It includes a server and a client script that enable two-way communication.

## Getting Started

### Prerequisites

- Python 3.x

### Installation

1. Clone the repository or download the scripts.

2. Ensure you have Python 3 installed on your machine.

### Running the Application

#### Server Side

1. Open a terminal and navigate to the directory containing the server script.

2. Run the server script:
    ```bash
    python server.py
    ```

#### Client Side

1. Open another terminal and navigate to the directory containing the client script.

2. Run the client script:
    ```bash
    python client.py
    ```

### Code Overview

#### Server Side

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(('localhost', 9999))

server.listen()

client, addr = server.accept()

done = False

while not done:
    msg = client.recv(1024).decode('utf-8')
    if msg == 'quit':
        done = True
    else:
        print(msg)
    client.send(input('Message: ').encode('utf-8'))
```

This script sets up a server that listens on `localhost` at port `9999`. It accepts a connection from a client and enters a loop to receive and send messages. The loop terminates when the message `quit` is received.

#### Client Side

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(('localhost', 9999))

done = False

while not done:
    client.send(input('Message: ').encode('utf-8'))
    msg = client.recv(1024).decode('utf-8')
    if msg == 'quit':
        done = True
    else:
        print(msg)
```

This script sets up a client that connects to the server at `localhost` on port `9999`. It enters a loop to send and receive messages, terminating when the message `quit` is received.

### Usage

1. Start the server script first.
2. Start the client script.
3. Type messages in the client terminal and observe them in the server terminal.
4. Type responses in the server terminal and observe them in the client terminal.
5. To end the chat, type `quit` in either terminal.

### License

This project is licensed under the MIT License.

### Acknowledgments

- Python documentation on the socket library.

---
