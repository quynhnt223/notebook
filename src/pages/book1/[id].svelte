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