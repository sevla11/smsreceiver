# SMS Receiver with SMS Retriever API
This is simple library for receiving sms in android with new SMS Retriever API.

[![](https://jitpack.io/v/pravinkumarputta/smsreceiver.svg)](https://jitpack.io/#pravinkumarputta/smsreceiver)


# Usage
### Step 1. Add the JitPack repository to your build file
Add it in your root build.gradle at the end of repositories:
```
allprojects {
	repositories {
		...
		maven { url 'https://www.jitpack.io' }
	}
}
```
### Step 2. Add the dependency
```
dependencies {
	implementation 'com.github.pravinkumarputta:smsreceiver:0.1.0'
}
```
### Step 3. Instantiate SMSReceiver
```
SMSBroadcastReceiver.OTPReceiveListener smsReceiverCallback = new SMSBroadcastReceiver.OTPReceiveListener() {
	@Override
	public void onSMSReceiverStarted() {

	}

	@Override
	public void onSMSReceiverFailed(Exception exception) {

	}

	@Override
	public void onSMSReceived(String message) {

	}

	@Override
	public void onSMSReceiverTimeOut() {

	}
};

SMSReceiver smsReceiver = SMSReceiver(activity, smsReceiverCallback)
```
### Step 3. Call startSmsListener() method to start receiving
```
smsReceiver.startSmsListener() // It stops receiving after one message received
```
# Construct a verification message
The verification message that you will send to the user's device. This message must:
	- Be no longer than 140 bytes
	- Begin with the prefix <#>
	- Contain a one-time code that the client sends back to your server to complete the verification flow (see Generating a one-time code)
	- End with an 11-character hash string that identifies your app (see Computing your app's hash string)
Otherwise, the contents of the verification message can be whatever you choose. It is helpful to create a message from which you can easily extract the one-time code later on. For example, a valid verification message might look like the following:
```
<#> Your ExampleApp code is: 123ABC78
FA+9qCX9VSu
```

(For more information visit [__here__](https://github.com/code-mc/material-icon-lib/blob/master/materialiconlib/src/main/assets/materialdesignicons-webfont.ttf?raw=true))
# Generating 11-character hash string for your app
After instantiating SMSReceiver access hash string using:
```
SMSReceiver.hashKey // After instantiating SMSReceiver othersise it returns empty string
```
