<script>
    import { onMount } from 'svelte';
    import { v4 as uuidv4 } from 'uuid';
    import { app } from "/src/firebase/init.js"
    import { getStorage, ref, uploadBytesResumable, getDownloadURL } from "firebase/storage";
    
    let blob
    let downloadURL2
    const storage = getStorage(app);
    let time
   
    
    function uploadfile() {
    
    const currentDate = uuidv4();
    const storageRef = ref(storage, "audio2s/" + currentDate + ".mp3");
    
    const uploadTask = uploadBytesResumable(storageRef, blob);
// logs: true
    uploadTask.on('state_changed', 
                        (snapshot) => {
                            // Observe state change events such as progress, pause, and resume
                            // Get task progress, including the number of bytes uploaded and the total number of bytes to be uploaded
                            const progress = (snapshot.bytesTransferred / snapshot.totalBytes) * 100;
                            console.log('Upload is ' + progress + '% done');
                            switch (snapshot.state) {
                            case 'paused':
                                console.log('Upload is paused');
                                break;
                            case 'running':
                                console.log('Upload is running');
                                break;
                            }
                        }, 
                        (error) => {
                            // Handle unsuccessful uploads
                        }, 
                        () => {
                            // Handle successful uploads on complete
                            // For instance, get the download URL: https://firebasestorage.googleapis.com/...
                            getDownloadURL(uploadTask.snapshot.ref).then((downloadURL) => {
                            console.log('File available at', downloadURL);
                            
                            downloadURL2 = downloadURL
                            console.log(downloadURL2)
                            document.getElementById("myaudio").load()
                            .then (
                                time = document.getElementById("myaudio").duration
                            )
                            
                            
                            });
                            
                        }
                       
                        );
   }
    
    
    
    onMount(async () => {
	(function recorder() {
	var a, i, b, c, d, f, g, h, l = ["start", "stop", "pause", "resume"],
		m = ["audio/webm", "audio/ogg", "audio/wav"],
		j = 1024,
		k = 1 << 20;

	function n(e) {
		var r, $ = Math.abs(e);
		return $ >= k ? (r = "MB", e /= k) : $ >= j ? (r = "KB", e /= j) : r = "B", e.toFixed(0).replace(/(?:\.0*|(\.[^0]+)0+)$/, "$1") + " " + r
	}

	function e(e) {
		i.innerHTML = "", navigator.mediaDevices.getUserMedia({
			audio: !0
		}).then(function(r) {
			a = new MediaRecorder(r), l.forEach(function(e) {
				a.addEventListener(e, t.bind(null, e))
			}), a.addEventListener("dataavailable", s), "full" === e ? a.start() : a.start(1e3)
		}), c.blur(), b.blur()
	}

	function o() {
		a.stop(), a.stream.getTracks()[0].stop(), g.blur()        
	}

	function p() {
		a.pause(), d.blur()
	}

	function q() {
		a.resume(), f.blur()
	}

	function r() {
		a.requestData(), h.blur()
	}

	function s(e) {
		var r = document.createElement("li"),
			$ = document.createElement("strong");
		$.innerText = "dataavailable: ", r.appendChild($);
		var a = document.createElement("span");
		a.innerText = e.data.type + ", " + n(e.data.size), r.appendChild(a);
		var o = document.createElement("audio");
		o.controls = !0, o.src = URL.createObjectURL(e.data), r.appendChild(o), i.appendChild(r)
	blob = e.data
    uploadfile()    
   
    }

	function t(e) {
		var r = document.createElement("li");
		r.innerHTML = "<strong>" + e + ": <\/strong>" + a.state, "start" === e && (r.innerHTML += ", " + a.mimeType), i.appendChild(r), "recording" === a.state ? (c.disabled = !0, b.disabled = !0, h.disabled = !1, f.disabled = !0, d.disabled = !1, g.disabled = !1) : "paused" === a.state ? (c.disabled = !0, b.disabled = !0, h.disabled = !1, f.disabled = !1, d.disabled = !0, g.disabled = !1) : "inactive" === a.state && (c.disabled = !1, b.disabled = !1, h.disabled = !0, f.disabled = !0, d.disabled = !0, g.disabled = !0)
	}
	i = document.getElementById("list"), c = document.getElementById("sec"), b = document.getElementById("record"), h = document.getElementById("request"), f = document.getElementById("resume"), d = document.getElementById("pause"), g = document.getElementById("stop"), MediaRecorder.notSupported ? (i.style.display = "none", document.getElementById("controls").style.display = "none", document.getElementById("formats").style.display = "none", document.getElementById("mode").style.display = "none", document.getElementById("support").style.display = "block") : (document.getElementById("formats").innerText = "Format: " + m.filter(function(e) {
		return MediaRecorder.isTypeSupported(e)
	}).join(", "), c.addEventListener("click", e.bind(null, "parts")), b.addEventListener("click", e.bind(null, "full")), h.addEventListener("click", r), f.addEventListener("click", q), d.addEventListener("click", p), g.addEventListener("click", o), c.disabled = !1, b.disabled = !1);
})();
    });
	</script>



<main>
    <p><a href="https://github.com/ai/audio-recorder-polyfill">Audio Recorder Polyfill</a> is&nbsp;a&nbsp;MediaRecorder polyfill to&nbsp;record&nbsp;audio in Edge and Safari. See <a href="https://ai.github.io/audio-recorder-polyfill/api">API</a>.</p>
    <div id="controls">
        <button id="record" title="Record"><svg viewbox="0 0 100 100">
        <circle cx="50" cy="50" r="46"></circle></svg></button><button id="sec" title="Record by 1 second"><svg viewbox="0 0 100 100">
        <circle cx="50" cy="50" r="46"></circle>
        <text font-size="45" x="26" y="64">
            1s
        </text></svg></button><button disabled id="pause" title="Pause"><svg viewbox="0 0 100 100">
        <rect height="80" width="25" x="14" y="10"></rect>
        <rect height="80" width="25" x="62" y="10"></rect></svg></button><button disabled id="resume" title="Resume"><svg viewbox="0 0 100 100">
        <polygon points="10,10 90,50 10,90"></polygon></svg></button><button disabled id="stop" title="Stop"><svg viewbox="0 0 100 100">
        <rect height="76" width="76" x="12" y="12"></rect></svg></button><button disabled id="request" title="Request data"><svg viewbox="0 0 100 100">
        <polygon points="10,10 90,10 50,90"></polygon></svg></button>
    </div>
    <div id="mode">
        Native support, <a href="https://ai.github.io/audio-recorder-polyfill/?polyfill">force polyfill</a>
    </div>
    <div id="formats">
        Format: audio/webm
    </div>
    <div id="support">
        Your browser doesn’t support MediaRecorder or&nbsp;WebRTC to be able to polyfill MediaRecorder.
    </div>
    <ul id="list"></ul>
</main>
{downloadURL2}
<h1>{time}</h1>
<audio id="myaudio" controls >
    <source type="audio/ogg"  src={downloadURL2}>   
</audio>
<style>
*{padding:0;margin:0}a{color:#009387}a:visited{color:#930087}body{margin:1rem;font-family:sans-serif}main{max-width:28rem;margin:0 auto;position:relative}#controls{display:flex;margin-top:2rem}button{flex-grow:1;height:2.5rem;min-width:2rem;border:none;border-radius:.15rem;background:#00e5d2;margin-left:2px;box-shadow:inset 0 -.15rem 0 rgba(0,0,0,.2);cursor:pointer;display:flex;justify-content:center;align-items:center}button:focus,button:hover{outline:none;background:#00ffe9}button::-moz-focus-inner{border:0}button:active{box-shadow:inset 0 1px 0 rgba(0,0,0,.2);line-height:3rem}button:disabled{pointer-events:none;background:#d3d3d3}button:first-child{margin-left:0}button svg{transform:translateY(-.05rem);fill:#000;width:1.4rem}button:active svg{transform:translateY(0)}button:disabled svg{fill:#9a9a9a}button text{fill:#00e5d2}button:focus text,button:hover text{fill:#00ffe9}button:disabled text{fill:#d3d3d3}#formats,#mode{margin-top:.5rem;font-size:80%}#mode{float:right}#support{display:none;margin-top:2rem;color:red;font-weight:700}#list{margin-top:1.6rem}audio{display:block;width:100%;margin-top:.2rem}li{list-style:none;margin-bottom:1rem}
</style>
