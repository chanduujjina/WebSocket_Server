sequenceDiagram
    autonumber
    participant Client
    participant WebSocketServer
    participant BackendService
    participant Database

    Client->>WebSocketServer: Connect to WebSocket
    WebSocketServer-->>Client: Connection Established

    Client->>WebSocketServer: Send Message
    WebSocketServer->>BackendService: Process Message
    BackendService->>Database: Query / Update Data
    Database-->>BackendService: Result
    BackendService-->>WebSocketServer: Response
    WebSocketServer-->>Client: Send Response

    BackendService->>WebSocketServer: Publish Event
    WebSocketServer-->>Client: Push Real-Time Event

    Client->>WebSocketServer: Close Connection
    WebSocketServer-->>Client: Connection Closed

