<script>
    import { onMount } from 'svelte';
    import { url } from '@roxi/routify'
    import Home from "../../components/icons/Home.svelte";
    import Menu from "../../components/icons/Menu.svelte";
    import {app} from "../../firebase/init.js"
    import { getFirestore, doc, setDoc, getDoc, onSnapshot, collection } from "firebase/firestore";
    
    const db = getFirestore(app);
    const url1 = $url()
    function realtime() {       
        const cityRef = doc(db, 'cities', url1);
        setDoc(cityRef, { capital: true }, { merge: true });
    }
    realtime()
    export let cool 
    const docref = doc(db, "cities", url1);
    getDoc(docref)
    .then((doc) => {
        cool = doc.id
    })
  
  onMount(async () => {
    console.log($url())
	});

</script>

<div class="content-wrap">
    <div class="content-header">
        
        <Home />
        {cool}	
        <Menu />
    </div>
    <div class="content">
        <slot name="content"></slot>	
    </div>
    
</div>
<style>
    .content-wrap{
    position: fixed;
    left:286px;
    right: 0;
    top: 0;
    bottom: 0;
    overflow: auto;
    
}
.content {
    background-color: #fff;
    min-height: 100vh;
    margin-top: 100px;
    margin-left: 12px;
    margin-right: 12px;
    border-radius: 6px;
    padding: 12px;
}
.content-header {
    position: fixed;
    background: #ffffff;
    height: 68px;
    top: 12px;
    left: 298px;
    right: 12px;
    border-radius: 6px;
    z-index: 999;
    box-shadow: 0.2rem 0.2rem 0.4rem #c8d0e7, -1px -1px 2px 0px #FFFFFFF7;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 12px;
    padding-right: 12px;
    font-size: 18px;
    font-weight: 700;
}
</style>