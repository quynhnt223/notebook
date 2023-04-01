<script>
    import { app } from "/src/firebase/init.js"
    import { v4 as uuidv4 } from 'uuid';
    import { getStorage, ref, uploadBytesResumable, getDownloadURL } from "firebase/storage";

    const storage = getStorage(app);
    
    

    
    let me
    
    document.addEventListener('paste', function (evt) {
        const currentDate = uuidv4();
        const storageRef = ref(storage, "images/" + currentDate);  
        console.log(currentDate)              
        
                    const clipboardItems = evt.clipboardData.items;
                    const items = [].slice.call(clipboardItems).filter(function (item) {
                        // Filter the image items only
                        return item.type.indexOf('image') !== -1;
                    });
                    if (items.length === 0) {
                        return;
                    }

                    const item = items[0];
                    const blob = item.getAsFile();

                    const imageEle = document.getElementById('preview');
                    imageEle.src = URL.createObjectURL(blob);
                    const uploadTask = uploadBytesResumable(storageRef, blob);


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
                            
                            me = downloadURL
                            
                            
                            });
                            
                        }
                       
                        );
                       


    });



    // Data URL string

// 'file' comes from the Blob or File API



</script>
<div class="container">
    <div>
        <div><kbd class="key">Ctrl</kbd> + <kbd class="key">V</kbd> in this window.</div>
        <img class="preview" id="preview" />

    </div>
</div>
<img src={me}>