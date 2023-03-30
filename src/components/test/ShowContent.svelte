<script>
    import { afterPageLoad } from "@roxi/routify"
    import { url } from '@roxi/routify'
    import {app} from "/src/firebase/init.js"
    import {getFirestore, doc, onSnapshot } from "firebase/firestore";
    import Accordion from "../../Accordion.svelte";

    const db = getFirestore(app);    

    let title
    let section01
    let section02
    let section03
    let section04
    let section05
    let section06
    let section07
    let section08
    let section09
    let section10
  
    let section01title
    let section02title
    let section03title
    let section04title
    let section05title
    let section06title
    let section07title
    let section08title
    let section09title
    let section10title


    $afterPageLoad(page => { 
        const PageId = $url().split("/").pop()
        const noteRef = doc(db, 'notes', PageId);    
        
        onSnapshot(noteRef, (doc) => {
            title = doc.data().title
            section01 =  doc.data().section01
            section02 =  doc.data().section02
            section03 =  doc.data().section03
            section04 =  doc.data().section04
            section05 =  doc.data().section05
            section06 =  doc.data().section06
            section07 =  doc.data().section07
            section08 =  doc.data().section08
            section09 =  doc.data().section09
            section10 =  doc.data().section10

            section01title =  doc.data().section01title
            section02title =  doc.data().section02title
            section03title =  doc.data().section03title
            section04title =  doc.data().section04title
            section05title =  doc.data().section05title
            section06title =  doc.data().section06title
            section07title =  doc.data().section07title
            section08title =  doc.data().section08title
            section09title =  doc.data().section09title
            section10title =  doc.data().section10title            
                
                
        });
    });
</script>
{#if title === undefined}
    <div>dasdas</div>
{/if}
<div class="content-wrap">
    <div class="content-header">
        <div class="title">{title}</div>
    </div>
    <div class="content">        
        <Accordion>
            <div slot="head">{@html section01title}</div>
            <div slot="details">{@html section01}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section02title}</div>
            <div slot="details">{@html section02}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section03title}</div>
            <div slot="details">{@html section03}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section04title}</div>
            <div slot="details">{@html section04}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section05title}</div>
            <div slot="details">{@html section05}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section06title}</div>
            <div slot="details">{@html section06}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section07title}</div>
            <div slot="details">{@html section07}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section08title}</div>
            <div slot="details">{@html section08}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section09title}</div>
            <div slot="details">{@html section09}</div>
        </Accordion>
        <Accordion>
            <div slot="head">{@html section10title}</div>
            <div slot="details">{@html section10}</div>
        </Accordion>
    </div>    
</div>
<style>
.title {
    font-weight: 700;
    color: #2C6556;
}
textarea:focus {
    outline: none;
}
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
:global(.header h5){
    background:#fff;
    padding:12px;
    border-radius: 8px;
    font-size: 18px;
    margin: 0;
    box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
    
}
:global(.header h5 span){
width:32px;
height: 32px;
border-radius: 50px;
background-color: rgb(64, 76, 64);
display: inline-block;
text-align: center;
line-height: 32px;
color: #fff;
margin-right: 12px;
font-weight: 300;
}
:global(code) {
    border-radius: 6px;
    padding: 20px!important;
}
.details {
    padding: 0;
}
</style>