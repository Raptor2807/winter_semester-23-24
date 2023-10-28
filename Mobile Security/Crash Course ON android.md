### Log Messaging
- One way to see whats happening inside an App is through Log Messaging.
- Android studio has it's own log system called Logcat which is essentially connected to our emulated device at displayed port. 
- You can also attach certain filters to output of Logcat. For example : *package:mine* - filters debugging information we received from our own application.
- To interact with Logcat we simply write a log function in *MainActivity.java* 
- *Log.d* - is our interface to this. 
	- It also has three parameter option. for example in a *catch* clause you can also *Throw* the exception into the log.
	`Log.d("My_Application", "This is a msg");`
### ADB Interface {Android Debugging Interface}
- Sometime when we need to install - uninstall android applications, it is easier to do it from the command line through direct dealing with ADB Interface. 
- we can use ADB to see logs of the device by using `adb logcat`
- However when using more than one emulated devices always use the process's IP and port as the id, like: `adb -s 192.168.232.2:5555 <command>`
- 


