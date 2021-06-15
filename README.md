# ExoMedia2
============
[//]: # (SEO terms: Simple ExoPlayer, ExoPlayer TextureView, ExoPlayer SurfaceView, ExoPlayer VideoView, ExoPlayer Audio)
ExoMedia2 is a media playback library with similar APIs to the Android MediaPlayer
and VideoView that uses the [ExoPlayer][ExoPlayer] as a backing when possible, 
otherwise the default Android MediaPlayer and VideoView are used.

The [ExoPlayer][ExoPlayer] is only supported on devices that pass the [compatibility Test Suite][CTS]
and that are JellyBean (API 16) or greater.  The [ExoPlayer][ExoPlayer] provides 
additional support for streaming (HLS, DASH, etc.) and full HD (1080p +) 

Use

```gradle
dependencies {
    implementation 'com.github.alexto9090:ExoMedia2:1.0'
}
```

Example
-------
The ExoMedia2 VideoView can be added in your layout files like any other Android view.

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
                xmlns:app="http://schemas.android.com/apk/res-auto"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

	<com.devbrackets.android.exomedia.ui.widget.VideoView
		android:id="@+id/video_view"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		app:useDefaultControls="true"/>
		
</RelativeLayout>
```

While in your Activity or Fragment you treat it like a standard Android VideoView

```java
private VideoView videoView;

private void setupVideoView() {
	// Make sure to use the correct VideoView import
	videoView = (VideoView)findViewById(R.id.video_view);
	videoView.setOnPreparedListener(this);

    //For now we just picked an arbitrary item to play
    videoView.setVideoURI(Uri.parse("https://archive.org/download/Popeye_forPresident/Popeye_forPresident_512kb.mp4"));
}

@Override
public void onPrepared() {
	//Starts the video playback as soon as it is ready
	videoView.start();
}
```
