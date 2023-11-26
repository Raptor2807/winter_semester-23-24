- Let's start with the big picture. 
- 1: [[Applications]]
	- Third party applications
		- Installed by the user himself from play-store, app store, etc
	- A few core ("system") applications (cannot be un-installed) 
		- Special flag is there for such kind of applications in package manager to mark them as system applications
		- Complement the implementation of the application framework API
			- Contacts management, initiating phone calls, SMS/MMS management,…
- 2: [[Application Packages]]
	- APK is simply a packaging format such as ZIP, TAR, GZ, etc
	- It contains all the "Components" of application such as: 
		- Activity - User Interface
		- Service - Background Service
		- Content Provider - SQL - Like Database
		- Broadcast Receiver - Mail box for Broadcasted messages
	- Applications can contain native code (C/C++ shared libraries) and resources
		- Native code provided as shared library files that can be dynamically linked into the process
		- Resources and assets: 
			- String values, 
			- layout definitions, 
			- drawables (pictures), 
			- raw data
	- META-INF/ contains the application certificate and package manifest
		- Package manifest not to be mistaken with the application manifest
			- [[Difference between package manifest vs application manifest]]
- 3: [[Application Manifest.xml]]
	- Declares application meta-data and all components
		- Names, Filters, Permissions
	- Example
		- ```
```<manifest xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools">
	<application
	******************************1***********************************
		android:icon="@mipmap/ic_launcher"
		android:label="@string/app_name”
		...
		android:roundIcon="@mipmap/ic_launcher_round"
		tools:targetApi="31">
	*******************************2**********************************	
		<activity android:name=".MainActivity”
			android:exported="true">
			<intent-filter>
				<action android:name="android.intent.action.MAIN" />
				<category android:name="android.intent.category.LAUNCHER" />
			</intent-filter>
		</activity>
	********************************3*********************************
		<receiver android:name=”.MyReceiver" >
			<intent-filter>
				<action android:name="android.intent.action.BOOT_COMPLETED" />
			</intent-filter>
		</receiver>
	*****************************************************************
		...
	</application>
</manifest>
```
Parts of the code named :- 1 : - App Info | 2 : Activity Component | 3 : Broadcast Receiver Component 
### [[Activity Component]]
- Represents a single screen in your application
	- Composed of different Views(Buttons, lists, text, etc)
	- Can be split into different Fragments (reusable UI modules with own life cycle, hosted by an Activity/Fragment in a hierarchy)
- 