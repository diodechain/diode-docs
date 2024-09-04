---
_schema: default
title: Diode WebSocket API Python Example (subscribe_channel)
nav_title:
SEO_options:
  title: Diode App Secure Messenger
  image:
  description:
draft: false
---
This is an example python script demonstrating how to use the Diode API with websockets:

```
import asyncio
import json
import logging
import os
import sys
import websockets
import websockets.exceptions
from jsonrpcclient import request, parse, Ok

bearer_token = "REPLACE"
zone_id = "REPLACE"
channel_id = "REPLACE"
device_id = "REPLACE"
diode_url = f"https://{device_id}.diode.link/api/json_rpc"
diode_wss_uri = f"wss://{device_id}.diode.link/api/json_rpc/ws"
method_send_msg = "send_message"
method_auth = "authenticate"
method_subscribe = "subscribe_channel"
method = method_send_msg


def base_payload():
    return {"jsonrpc": "2.0", "id": 1}


def handle_exception(e):
    if isinstance(e, websockets.exceptions.WebSocketException):
        print(f"WebSocket error: {e}")
    elif isinstance(e, websockets.exceptions.ConnectionClosedError):
        print(f"Conn closed unexpectedly: {e}")
    elif isinstance(e, json.JSONDecodeError):
        print(f"JSON decoding err: {e}")
    elif isinstance(e, asyncio.TimeoutError):
        print(f"Timed out request: {e}")
    else:
        print(f"An unexpected error occurred: {e}")


async def send_auth(websocket):
    params = [bearer_token]
    payload = base_payload()
    payload["method"] = method_auth
    payload["params"] = params
    message = json.dumps(payload)
    await websocket.send(message)
    response = await websocket.recv()
    return json.loads(response)


async def subscribe_channel(websocket):
    params = [zone_id, channel_id]
    payload = base_payload()
    payload["method"] = method_subscribe
    payload["params"] = params
    message = json.dumps(payload)
    await websocket.send(message)
    response = await websocket.recv()
    return json.loads(response)


# message receiver
async def receive_messages():
    try:
        print(diode_wss_uri)
        async with websockets.connect(diode_wss_uri) as websocket:
            try:
                # initial authentication
                resp = await send_auth(websocket)
                print(resp)

                # subscribe to the diode channel
                resp = await subscribe_channel(websocket)
                print(resp)

            except Exception as e:
                handle_exception(e)
                sys.exit(1)

            while True:
                message = await websocket.recv()
                print(f"Received message: {message}")

    except KeyboardInterrupt:
        print("Program exit. Interrupted by user")
    except Exception as e:
        print(f"An error occurred upon connection attempt: {e}")


# main loop
asyncio.run(receive_messages())
```