# Mesibo_sample_app

## issue:

we are using `mesibo_flutter_sdk v2.2.9`, it was working normally but after we added `firebase_messaging v14.7.20`\
we found that `Mesibo_onConnectionStatus` method was no longer getting called after starting `mesibo`\
specifically we found that following line is causing the issue, if we comment it out, it works normally
```dart 
FirebaseMessaging.onBackgroundMessage(_handleBackgroundMessage);
```

we have created a minimal reproducible code sample, you can try running it with `FirebaseMessaging.onBackgroundMessage(_handleBackgroundMessage);`
commented out and see that `mesibo` is working but if we enable that line then `mesibo` does not work.

we also have added a simple platform channel `methodChannelExample` with method `getMsg` which we call when we click on the Floating action button,\
it will print `hello from method channel` in console if the call was successful , this is to demonstrate that even when `mesibo` is not working, our platform channel works, which disproves the speculation that `firebase_messaging v14.7.20` is causing the platform channel to close/terminate or misbehave.

