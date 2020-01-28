# TabUtils
Multiple browser tabs communication, locking and synchronization component (same-origin). Based on localStorage object.

One small file, zero dependencies.

### Features:

* executing "interlocked" function call - runs only once across multiple tabs
* broadcasting a message to all tabs (including the current one) along with some "data" string
* ...and handling the "broadcasted message" event

## Usage 

```html
<script src="https://cdn.jsdelivr.net/gh/jitbit/TabUtils/TabUtils.js"></script>

<script>

    //locked "critical section" code - runs only once
    TabUtils.CallOnce("lockname", function () { alert("I run only once in multiple tabs"); }, timeout);
    //"timeout" above is optional (for how long to hold the lock - in milliseconds)

    //handle a broadcasted message
    TabUtils.OnBroadcastMessage("eventName", function (eventDataString) { DoSomething(); });

    //sends a broadcast message to all tabs, including the current tab too!
    TabUtils.BroadcastMessageToAllTabs("eventName", eventDataString);

    //P.S. standard localStorage events are not being sent to current tab, only OTHER tabs.
    //This component sends the message to ALL tabs

</script>
```

Make sure you register the event handler BEFORE sending a broadcasted message.

Contributions are very welcome.

&copy; [Jitbit](https://jitbit.github.com/)
