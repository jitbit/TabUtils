# TabUtils
Multiple browser tabs communication, locking and synchronization component. Based on localStorage object.

### Features:

* executing "interlocked" function call - runs only once per multiple tabs
* broadcasting a message to all tabs (including the current one) along with some message "data" string
* handling a "broadcasted message" event

## Usage 

```JavaScript
<script src="TabUtils.js"></script>

<script>

//interlocked call - runs code only once
TabUtils.CallOnce("lockname", function () { alert("I run only once in multiple tabs"); });

//handle a broadcasted message
TabUtils.OnBroadcastMessage("eventName", function (eventDataString) { DoSomething(); });

//sends a broadcast message to all tabs, including the current tab too!
TabUtils.BroadcastMessageToAllTabs("eventName", eventDataString);

//P.S. standard localStorage events are not sent to current tab, only OTHER tabs.
//This component sends the message to ALL tabs

</script>
```

Make sure you register the event handler BEFORE sending a broadcasted message.

Contributions are very welcome.

Dependencies: jQuery
