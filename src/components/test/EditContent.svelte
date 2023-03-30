<script>
import { afterPageLoad } from "@roxi/routify"
import { url } from '@roxi/routify'
import {app} from "/src/firebase/init.js"
import {getFirestore, doc, setDoc, onSnapshot} from "firebase/firestore";

let active = false;

const db = getFirestore(app);
let addDoc

let title = ""
let section01 = ""
let section02 = ""
let section03 = ""
let section04 = ""
let section05 = ""
let section06 = ""
let section07 = ""
let section08 = ""
let section09 = ""
let section10 = ""

let section01title = ""
let section02title = ""
let section03title = ""
let section04title = ""
let section05title = ""
let section06title = ""
let section07title = ""
let section08title = ""
let section09title = ""
let section10title = ""


$afterPageLoad(page => { 
    
    const PageId = $url().split("/").pop()
    const noteRef = doc(db, 'notes', PageId);

    addDoc = function adddoc() {            
        setDoc(
                noteRef,
                {
                    title: title,
                    section01: section01,
                    section02: section02,
                    section03: section03,
                    section04: section04,
                    section05: section05,
                    section06: section06,
                    section07: section07,
                    section08: section08,
                    section09: section09,
                    section10: section10,
                    section01title: section01title,
                    section02title: section02title,
                    section03title: section03title,
                    section04title: section04title,
                    section05title: section05title,
                    section06title: section06title,
                    section07title: section07title,
                    section08title: section08title,
                    section09title: section09title,
                    section10title: section10title,
                }, { merge: true }
            );
            
    }; 
      
    
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
<button   class="editbtn" on:click="{() => active = !active}">edit</button>
<div  class:active={active} class="wrap">
    <button on:click={addDoc}>Add Doc</button>
<form>
    <div>Title</div>
    <input class="title" bind:value={title} type="text" placeholder="Title">
    <div>Section 01</div>
    <input bind:value={section01title}>
    <textarea bind:value={section01}></textarea>
    <div>Section 02</div>
    <input bind:value={section02title}>
    <textarea bind:value={section02}></textarea>
    <div>Section 03</div>
    <input bind:value={section03title}>
    <textarea bind:value={section03}></textarea>
    <div>Section 04</div>
    <input bind:value={section04title}>
    <textarea bind:value={section04}></textarea>
    <div>Section 05</div>
    <input bind:value={section05title}>
    <textarea bind:value={section05}></textarea>
    <div>Section 06</div>
    <input bind:value={section06title}>
    <textarea bind:value={section06}></textarea>
    <div>Section 07</div>
    <input bind:value={section07title}>
    <textarea bind:value={section07}></textarea>
    <div>Section 08</div>
    <input bind:value={section08title}>
    <textarea bind:value={section08}></textarea>
    <div>Section 09</div>
    <input bind:value={section09title}>
    <textarea bind:value={section09}></textarea>
    <div>Section 10</div>
    <input bind:value={section10title}>
    <textarea bind:value={section10}></textarea>
</form>
</div>
<style>
.wrap {
    position: fixed;
    top: 0;
    right: 0;
    left: 600px;
    bottom: 0;
    z-index: 999999;
    background: #fff;
    overflow: auto;
    display: none;
    padding: 20px;
    box-shadow: rgba(0, 0, 0, 0.15) 0px 15px 25px, rgba(0, 0, 0, 0.05) 0px 5px 10px;
}
.editbtn{
    outline: none;
    border: none;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 99999999999;
    border-bottom-right-radius: 50px;
    color: transparent;
    box-shadow: rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset, rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset, rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, rgba(0, 0, 0, 0.06) 0px 2px 1px, rgba(0, 0, 0, 0.09) 0px 4px 2px, rgba(0, 0, 0, 0.09) 0px 8px 4px, rgba(0, 0, 0, 0.09) 0px 16px 8px, rgba(0, 0, 0, 0.09) 0px 32px 16px;
}
.editbtn:active, .editbtn:focus{border: none;}
.active {display: block;}
input {
border: none;
width: 100%;
text-align: center;
background-color: #ccc;
border-radius: 8px;
}
input:focus {
    outline: none;
}
textarea {    
    padding: 12px 20px;
    box-sizing: border-box;
    border: 2px solid #ccc;
    border-radius: 6px;
    background-color: #fff;
    font-size: 16px;
    resize: none;
    overflow: auto;
    border: none;
    background-color: #ccc;
    border-radius: 8px;
    width: 100%;
    height: 268px;
    
}
.title{background-color: aqua;}
@media only screen and (max-width: 600px) {
.wrap {
left: 0;
    }

}
</style>