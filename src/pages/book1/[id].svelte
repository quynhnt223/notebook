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
<ShowContent/>
<EditContent/>

<style>
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