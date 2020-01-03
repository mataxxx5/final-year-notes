---
tags: [FYP-Research]
title: OpenCV to Unity Approches
created: '2019-12-21T11:14:37.651Z'
modified: '2019-12-30T21:57:31.064Z'
---

# OpenCV to Unity Approches
> Investigative Diary into
## Socket to OpenCV Instance
> The idea behind this approach was to have and instance of OpenCV program running alongside Unity, the video capture from the camera would go to both openCV and Unity, then program would package up video processing data and transport it to Unity via socket

This approach has many distavantages:
- speed of data transmission though sockets
- sharing of visual information between unity and another service that can do video processing
- building an architecture that is unsuitable for mobile phones

## Native Plugin for Unity
> Unity has OpenCV plugin, sadly it's a paid for service and there's critique of it's performance when dealing wth realtime video. Upon investigation, I found that I could write C++/C based code and port it to Unity as a unmanaged plugin via .NET, this approach is faster than doing video processing via scripts in Unity

Existing Plugins:
 - [OpenCV for Unity](https://assetstore.unity.com/packages/tools/integration/opencv-for-unity-21088) - Paid for, extensive
 - [OpenCV plus Unity](https://assetstore.unity.com/packages/tools/integration/opencv-plus-unity-85928) - free and a great resource, however too big and has too many features for what's necessary, no longer supported

<strong>I picked this approach due to it's speed(machine code), reusability(native plugin for IOS and android)</strong> 

### Developing a Native Plugin 

Trial Run:
- Take code already written in python, compile it to cython
- compile it further to a c plugin for unity
- import it in unity and test functonionality



### Useful Resources
* [Using Native Plugin to Encapsulate OpenCV](https://www.reddit.com/r/gamedev/comments/3u7md4/native_plugins_can_speed_up_unity_games_by_a/)
* [Guide to Compiling DDL for Native Unity Plugins](https://www.reddit.com/r/gamedev/comments/3u7md4/native_plugins_can_speed_up_unity_games_by_a/)
* [Guide to building Unity C++ plugin for AR](https://www.youtube.com/watch?v=I4DthTlVAOU)

