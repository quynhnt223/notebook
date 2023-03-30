<script>
    import { url } from '@roxi/routify'    
    import { afterPageLoad } from "@roxi/routify"
    import {app} from "../../firebase/init.js"
    import { getFirestore, doc, setDoc, getDoc, onSnapshot, collection } from "firebase/firestore";
    import Home from '../../components/icons/Home.svelte';
    import Menu from '../../components/icons/Menu.svelte';
    import Navbar from './Navbar.svelte';
    import Accordion from '../../Accordion.svelte';
    import EditContent from '../../components/test/EditContent.svelte';
    import ShowContent from '../../components/test/ShowContent.svelte';
    

    let active = true;
	const handleClickmobile = () => display = !display;
	const handleClick = function open() {
        document.querySelector('#input1').style.display = "block";
        document.querySelector('.savebtn').style.display = "block";
        document.querySelector('.editbtn').style.display = "none";
        document.querySelector('#input1').focus()        
    }
    const close = function close() {
        document.querySelector('#input1').style.display = "none";  
        document.querySelector('.savebtn').style.display = "none";
        document.querySelector('.editbtn').style.display = "block";          
    }
    
    
    let haha = ""
    let name = ""
    let item = ""
    let adddoc
    let title = ""
    let addtitle
    
    
$afterPageLoad(page => {        
    console.log($url())
    const url1 = $url().split("/").pop()  
    const db = getFirestore(app);
    const cityRef = doc(db, 'cities', url1);
    
    addtitle = function addtitle(event) {
        if (event.key === "Enter") {
            setDoc(cityRef,
            {
                title: title
            }, { merge: true }
            );
        }        
    }
    adddoc = function adddoc() {     
        
        setDoc(cityRef, 
            {
                name: item
                
            }, { merge: true }
            );
    };        
    
    onSnapshot(cityRef, (doc) => {
            const cool = doc.data().name
            const cool2 = doc.data().capital
            const doctitle = doc.data().title
            title = doctitle
            haha = cool
            item = haha
            name = cool2
            
            
        })
    })
</script>
    <div  class:active={!active}><Navbar/></div>

<button  class="savebtn" on:click={adddoc} on:click={close}>Save</button>
<div class="textarea">
    <textarea id="input1" bind:value={item} ></textarea>    
    </div>




<ShowContent/>
<EditContent/>
<style>
.savebtn{display: none;z-index: 999999;}
#input1 {
    display: none;
}
button {
    position: absolute;
    right: 24px;
    top: 108px;
    z-index: 99;
}

textarea {
    position: fixed;
    top: 104px;
    bottom: 0;
    left: 298px;
    right: 12px;    
    padding: 12px 20px;
    box-sizing: border-box;
    border: 2px solid #ccc;
    border-radius: 6px;
    background-color: #fff;
    font-size: 16px;
    resize: none;
    overflow: auto;
    border: none;
    z-index: 9999;
    
}

input {
border: none;
width: 100%;
text-align: center;
}
input:focus {
    outline: none;
}
body{overflow: hidden;}
@media only screen and (max-width: 600px) {
.content-wrap{
    left:0;
}
.content-header {
    left: 0;
    top: 0;
    right: 0;
    border-radius: 0;
    box-shadow: none;
}

textarea {
left: 12px;
}
:global(body) {
    overflow: hidden!important;
}
}
:global(body) {
    overscroll-behavior: contain;
}
:global(.content .accordion) {
    box-shadow: none!important;
    margin-bottom: 6px!important;
    
    
}
:global(.content .accordion .header) {
    padding-left: 0!important;
    padding:0!important
    
}
:global(.content .accordion .details) {
  padding:12px!important;
    
}
:global(blockquote) {
  margin-top: 12px!important;
  max-width:440px;
  border-radius: 6px;
  padding: 12px!important;
  margin-left: 0!important;
  background-color: #ccc;
    
}
</style>