# SocketIO Manager Unity

Event based Communnication Manger for SocketIO

## Usage

* Drag SocketIO Manager from `Assets\SocketIOManager\Prefabs\SocketIO Manager.prefab` to Unity Scene
* Write event handler script and register it to Socket Manager

## Binding Event Example

```cs
using Facebook.Unity;
using System.Collections.Generic;
using UnityEngine;
using SocketIO;
using SocketIOManager;

namespace ARTag
{
    public class ExampleEventHandler : SocketManager
    {

        SocketManager socket;
        
        const string SAMPLE_EVENT = "sample";
        
        // Use this for initialization
        void Start()
        {
            socket = GameObject.FindObjectOfType<SocketManager>();
            socket.Register(gameObject);
            socket.On(SAMPLE_EVENT, OnSampleEvent);
        }

        void OnSampleEvent(SocketIOEvent e)
        {
            // Do something
            socket.Emit(SAMPLE_EVENT, sampleData);
        }

        void OnConnectionOpen(){
            // Do something when connection is openned.
        }
        
        void OnConnectionClose(){
            // Do something when connection is closed.
        }
        
        void OnConnectionError(){
            // Do something when connection is error.
        }
    }

}
```
