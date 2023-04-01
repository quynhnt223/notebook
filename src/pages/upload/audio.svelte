<script>
   	import { onMount } from 'svelte';
    import { v4 as uuidv4 } from 'uuid';
    import { app } from "/src/firebase/init.js"
    import { getStorage, ref, uploadBytesResumable, getDownloadURL } from "firebase/storage";
    
    
    let file
    let blobfile
    let files;
    let audiourl
    let me 
    let downloadURL2
    const storage = getStorage(app);

    

    



    function save() {
        var a = document.createElement( 'a' );
        a.download = 'recordme';
        a.href = audiourl;
        document.body.appendChild( a );
        a.click();

        document.body.removeChild( a );
    }

   function clickme() {
    console.log(file instanceof File);
    const currentDate = uuidv4();
    const storageRef = ref(storage, "audios/" + currentDate + ".mp3");
    
    const uploadTask = uploadBytesResumable(storageRef, me);
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
                            
                            });
                            
                        }
                       
                        );
   }
   
  
   
    
    
    onMount(async () => {
		

        const record = document.querySelector('#record');
        const stop = document.querySelector('#stop');
        const soundClips = document.querySelector('#sound-clips');
        const canvas = document.querySelector('#visualizer');
        const mainSection = document.querySelector('#main-controls');

        // disable stop button while not recording

        stop.disabled = true;

        // visualiser setup - create web audio api context and canvas Not done yet.

        // const audioCtx = new (window.AudioContext || webkitAudioContext)();
        // const canvasCtx = canvas.getContext("2d");

        //main block for doing the audio recording

        if (navigator.mediaDevices.getUserMedia) {
            console.log('getUserMedia supported.');

            let chunks = [];

            const onSuccess = (stream) => {

                const mediaRecorder = new MediaRecorder(stream);

                record.onclick = function () {
                    mediaRecorder.start();
                    stop.disabled = false;
                    record.disabled = true;
                    canvas.innerText = 'Cool waveform indicates recording here.'
                }

                stop.onclick = function () {
                    mediaRecorder.stop();
                    stop.disabled = true;
                    record.disabled = false;
                    canvas.innerText = ''
                }

                mediaRecorder.onstop = function (e) {
                    let clipContainer = document.createElement('article');
                    let audio = document.createElement('audio');
                    let deleteButton = document.createElement('button');
                    let saveButton = document.createElement('button')

                    clipContainer.classList.add('clip');
                    audio.setAttribute('controls', '');
                    deleteButton.textContent = 'Delete';
                    deleteButton.className = 'delete';
                    saveButton.textContent = 'Save File';
                    saveButton.className = 'save';

                    clipContainer.appendChild(audio);
                    clipContainer.appendChild(deleteButton);
                    clipContainer.appendChild(saveButton)
                    soundClips.appendChild(clipContainer);

                    audio.controls = true;
                    let blob = new Blob(chunks, { 'type': 'audio/mp3; codecs=opus' });
                    chunks = [];
                    let audioURL = window.URL.createObjectURL(blob);
                    audio.src = audioURL;
                    console.log("recorder stopped" + blob);

                    audiourl = audioURL
                    me = blob
                    clickme()
                    blobfile = blob

                    deleteButton.onclick = (e) => {
                        evtTgt = e.target;
                        evtTgt.parentNode.parentNode.removeChild(evtTgt.parentNode);
                    }

                    saveButton.onclick = (e) => {
                        console.log(blob)
                        alert(`Save sends this ${blob.size}-bit audio blob to server`)
                    }
                }

                mediaRecorder.ondataavailable = function (e) {
                    chunks.push(e.data);
                }
            } // onSuccess

            const onError = (err) => {
                console.log('The following error occured: ' + err);
            }

            navigator.mediaDevices.getUserMedia({ audio: true }).then(onSuccess, onError);

        } else {
            console.log('getUserMedia not supported on your browser!');
        }
});
</script>
<main>
    <section id="main-controls">
        <p id="visualizer"></p>
        <div id="buttons">
        <button id="record">Record</button>
        <button id="stop">Stop</button>
        </div>
    </section>
    <section id="sound-clips"></section>
</main>
<button on:click={save}>save me</button>
{downloadURL2}

