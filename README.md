## react-native-ksyplayer
 
> Source Type: **Open Source**

> Media Player for React-Native, base on KSYMediaPlayer.

More details about KSYMediaPlayer, please click the link blow:

* [KSYMediaPlayer Android SDK for vod or live streaming playing](https://github.com/ksvc/KSYMediaPlayer_Android)
* [KSYMediaPlayer iOS SDK for vod or live streaming playing](https://github.com/ksvc/KSYMediaPlayer_iOS)

*Android support*

*iOS support*

*Video Format Support:FLV, TS, MPEG, MOV, MP4, M4V, MP3, AAC, GIF, ASF, RM, MKV, AVI, WEBM, HLS, RTMP, RTSP, HTTP, FILE*

*Audio Format Support:AAC, MP3, NELLYMOSER, AMRNB, AMRWB, WMV1, WMV2, WMV3, OGG, FLAC, DTS, COOK*


### 1. About

A `<KSYVideo>` component for react-native,requires react-native >= 0.49.0

If you're interested in this library, I'd love to see you join in maintenance.

#### 1.1 Add it to your project
* Install via npm

Run `npm install react-native-ksyplayer --save`


### 1.2 Usage Example

```javascript

<KSYVideo source={{uri: "rtmp://"}}   // Can be a URL or a local file.
       ref={(ref) => {
         this.player = ref
       }}                                      // Store reference
  
       volume={1.0}                            
       rate={1.0}                              // rate
       muted={false}                           
       paused={false}                          // Pauses playback entirely.
       resizeMode="cover"                      // Fill the whole screen at aspect ratio.*
       repeat={true}                           // Repeat forever.
       playInBackground={false}                // Audio continues to play when app entering background.
       progressUpdateInterval={250.0}          // Interval to fire onProgress (default to ~250ms)
       onLoadStart={this.loadStart}            // Callback when video starts to load
       onLoad={this.setDuration}               // Callback when video loads
       onProgress={this.setTime}               // Callback every ~250ms with currentTime
       onEnd={this.onEnd}                      // Callback when playback finishes
       onError={this.videoError}               // Callback when video cannot be loaded
       onBuffer={this.onBuffer}                // Callback when remote video is buffering
       style={styles.backgroundVideo} />


// Later on in your styles..
const styles = StyleSheet.create({
  backgroundVideo: {
    position: 'absolute',
    top: 0,
    left: 0,
    bottom: 0,
    right: 0,
  },
});
```

### 2. Android Integration

Run `react-native link` to link the react-native-ksyplayer library.

Or if you have trouble, make the following additions to the given files manually:

**android/settings.gradle**

```gradle
include ':react-native-ksyplayer'
project(':react-native-ksyplayer').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-ksyplayer/android')
```

**android/app/build.gradle**

```gradle
dependencies {
   ...
   compile project(':react-native-ksyplayer')
}
```

**MainApplication.java**

On top, where imports are:

```java
import com.ksyun.media.reactnative.ReactKSYVideoPackage;
```

Add the `ReactKSYVideoPackage` class to your list of exported packages.

```java
@Override
protected List<ReactPackage> getPackages() {
    return Arrays.asList(
            new MainReactPackage(),
            new ReactKSYVideoPackage()
    );
}
```

### 3. iOS Integration

Run `react-native link` to link the react-native-ksyplayer library.

Add KSYMediaPlayer.framework(which is in node_modules/react-native-ksyplayer/ios directory) to your project setting 'target->Build Phases->Link Binary With Libraries'.

Add Framework Search Path : '../node_modules/react-native-ksyplayer/ios'


### 4. Remarks
If you want to updata native sdk for KSYVideo,make the following additions
#### 4.1 Android
The KSYVideo is dependented on [jcenter](https://bintray.com/ksvc/ksyplayer),you can modify the dependencies ,update to high version

build.gradle(Module:react-native-ksyplayer)
```gradle
dependencies {

    compile "com.facebook.react:react-native:+"  // From node_modules
    compile 'com.ksyun.media:libksyplayer-arm64:2.2.4'
    compile 'com.ksyun.media:libksyplayer-x86:2.2.4'
    compile 'com.ksyun.media:libksyplayer-armv7a:2.2.4'
    compile 'com.ksyun.media:libksyplayer-java:2.2.4'
}
```


#### 4.2 iOS

Get the latest framework of KSYMeidaPlayer_iOS at https://github.com/ksvc/KSYMediaPlayer_iOS/releases, then replace the old framework in node_modules/react-native-ksyplayer/ios directory

### 5. LICENSE
[Apache 2.0](LICENSE)


### 6. SDK
[player_android](https://github.com/ksvc/KSYMediaPlayer_Android)

[player_ios](https://github.com/ksvc/KSYMediaPlayer_iOS)

