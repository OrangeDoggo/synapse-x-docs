# Websocket Library

### Connecting
```syn
<object> syn.websocket.connect(<string> url)
```
Connects to the url specified. Errors if the connection fails.
## Class Methods
### Send
```syn
WebSocket:Send(<string> message)
```
Sends message to the server.
### Close
```syn
WebSocket:Close(<void>)
```
Closes the connection with the server.
## Events
### On Message
```syn
WebSocket.OnMessage
```
Event is fired when a message is sent from the server.
### On Close
```syn
WebSocket.OnClose
```
Event is fired when the WebSocket is closed (either by `WebSocket:Close` or by the server).

## Example
```lua
local WebSocket = syn.websocket.connect("ws://localhost:123/test") -- Specify your WebSocket URL here.

WebSocket.OnMessage:Connect(function(Msg)
    print(Msg) -- Print messages sent to SX.
end)

local Ctr = 1
while wait(1) do 
    WebSocket:Send("gamer vision " .. tostring(Ctr)) -- Send messages to the WebSocket server.
    WebSocket:Send("epic gamer vision " .. tostring(Ctr))
    WebSocket:Send("epicer gamer vision " .. tostring(Ctr))
    Ctr = Ctr + 1

    if Ctr == 150 then 
        WebSocket:Close() -- Close the websocket when you are done! (this is done implicitly on teleports aswell)
        do return end
    end
end
```