Tap the screen to start.

## What for?
I build this for my Android tablet to monitor various web resources, and experiment on graphics and WebGL.

## How it work?
The page "fixes" the auto dimming or screen timeout feature of Android OS, common for smartphones and tablets,
via a playback of an invisible video file, with the video source converted into a Base64 encoded data URI.
The fix or hack is at the cost of high power consumption. I have read this hack from the Internet, but
unfortunately, I have forgot its source.
```PowerShell
# Generate a video with 2x2 resolution via ffmpeg
ffmpeg -f lavfi -i "color=color=black[black_video];[black_video]scale=2:2" -t 1 -c:v libx264 black.mp4
# Generate Base64 encoded data URI for the web via PowerShell, and send the output to clipboard
$FileContent = Get-Content -Path black.mp4; $Bytes = [System.Text.Encoding]::Unicode.GetBytes($FileContent); "data:video/mp4;base64," + [Convert]::ToBase64String($Bytes) | Set-Clipboard
```

## What's next?
- For simple "cool" text effects, try to google "Neotext CSS cspen" etc. Copy, read and modify others code will give you a lots of "cool" text effects
- For more advanced users, check out:
	- Canvas API: https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API
		- p5js: https://p5js.org/
	- WebGL: https://get.webgl.org/
		- Threejs: https://threejs.org/
		- Shadertoy: https://www.shadertoy.com/
	- WASM (Use Rust etc.): https://webassembly.org/
	- Use Python: https://pyscript.net/
	
## License
MIT
