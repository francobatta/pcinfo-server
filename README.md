# pcinfo-server
## What's this?
A Node.js MQTT server leveraging the systeminformation lib (and/or orthers) in order to gather and publish desired PC info to MQTT clients.
## Why?
I want to use my old Android smartphone (a LG G2) as a "widget" in my PC case, displaying relevant data i.e. CPU temp, GPU temp, CPU usage, etc.

In order to do this I must first provide the data from my OS - [systeminformation](https://github.com/sebhildebrandt/systeminformation) is a great open source library which (in Windows OSs) reads directly from [wmic](https://docs.microsoft.com/en-us/windows/win32/wmisdk/wmic). Sadly my AMD processor/BIOS vendor hasn't implemented the necessary wmic calls, so I'd need an external program to do more work to provide a reading.

On the other hand, [Open Hardware Monitor](https://github.com/openhardwaremonitor/openhardwaremonitor) is a great library, plus it provides wmic with data through an interface. The thing with it is that communication with the client is through HTTP per-request basis, which seems less efficient and slower than MQTT here.
Besides, I haven't found an android client with a nice UI for this use case.

In short, I want to code a server which
- Provides wanted data from a PC (mainly temps, voltages, % of usage)
- Uses MQTT instead of HTTP
- Leverages existing libraries correctly, probably using command line arguments
- Supports reading from propietary components
