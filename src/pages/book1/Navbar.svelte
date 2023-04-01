
<script>
    import Accordion from "../../Accordion.svelte";    
    import Note from "../../components/icons/Note.svelte";
    import Content from "./Content.svelte";
    let active = false;
    import { url } from '@roxi/routify'

    
   
</script>
<button on:click="{() => active = !active}" class="open-nav"></button>
<div class:active={active} class="navbar">
<Accordion><!-- 1 -->
    <div slot="head"><span class="hn">01</span><span>Project Init</span></div>
    <div slot="details">    
        <a on:click="{() => active = false}" href="/book1/1"><Note/> Creating An App</a>
        <a on:click="{() => active = false}" href="/book1/2"><Note/> Add Manifest file</a>
        <a on:click="{() => active = false}" href="/book1/3"><Note/> Add App icons files</a>
        <a on:click="{() => active = false}" href="/book1/4"><Note/> Service-worker.js File</a>
        <a on:click="{() => active = false}" href="/book1/5"><Note/> Deploy to Firebase Hosting</a>
        <a on:click="{() => active = false}" href="/book1/6"><Note/> Command errors</a>
        <a on:click="{() => active = false}" href="/book1/7"><Note/> Deploy to Netlify</a>
        <a on:click="{() => active = false}" href="/book1/8"><Note/> Setup Git</a>
        <a on:click="{() => active = false}" href="/book1/9"><Note/> Don't tell me i am wrong</a>
        <a on:click="{() => active = false}" href="/book1/10"><Note/> Don't tell me i am wrong</a>
    </div>
</Accordion>
<Accordion><!-- 2 -->
    <div slot="head"><span class="hn">02</span><span>Firestore</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 3 -->
    <div slot="head"><span class="hn">03</span><span>Firebase Auth</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 4 -->
    <div slot="head"><span class="hn">04</span><span>Accordion</span></div>
	<div slot="details">
        <a on:click="{() => active = false}" href="/book1/4-1"><Note/> Creating An App</a>
        <a on:click="{() => active = false}" href="/book1/4-2"><Note/> Add Manifest file</a>
        <a on:click="{() => active = false}" href="/book1/4-3"><Note/> Add App icons files</a>
        <a on:click="{() => active = false}" href="/book1/4-4"><Note/> Service-worker.js File</a>
        <a on:click="{() => active = false}" href="/book1/4-5"><Note/> Deploy to Firebase Hosting</a>
        <a on:click="{() => active = false}" href="/book1/4-6"><Note/> Command errors</a>
        <a on:click="{() => active = false}" href="/book1/4-7"><Note/> Deploy to Netlify</a>
        <a on:click="{() => active = false}" href="/book1/4-8"><Note/> Setup Git</a>
        <a on:click="{() => active = false}" href="/book1/4-9"><Note/> Don't tell me i am wrong</a>
        <a on:click="{() => active = false}" href="/book1/4-10"><Note/> Don't tell me i am wrong</a>
       
    </div>
</Accordion>
<Accordion><!-- 5 -->
    <div slot="head"><span class="hn">05</span><span>Fix Errors</span></div>
	<div slot="details">
        <a on:click="{() => active = false}" href="/book1/5-1"><Note/> Fix undefined values</a>
        <a on:click="{() => active = false}" href="/book1/5-2"><Note/> Add Manifest file</a>
        <a on:click="{() => active = false}" href="/book1/5-3"><Note/> Add App icons files</a>
        <a on:click="{() => active = false}" href="/book1/5-4"><Note/> Service-worker.js File</a>
        <a on:click="{() => active = false}" href="/book1/5-5"><Note/> Deploy to Firebase Hosting</a>
        <a on:click="{() => active = false}" href="/book1/5-6"><Note/> Command errors</a>
        <a on:click="{() => active = false}" href="/book1/5-7"><Note/> Deploy to Netlify</a>
        <a on:click="{() => active = false}" href="/book1/5-8"><Note/> Setup Git</a>
        <a on:click="{() => active = false}" href="/book1/5-9"><Note/> Don't tell me i am wrong</a>
        <a on:click="{() => active = false}" href="/book1/5-10"><Note/> Don't tell me i am wrong</a>
       
    </div>
</Accordion>
<Accordion><!-- 6 -->
    <div slot="head"><span class="hn">06</span><span>Firebase Storage</span></div>
	<div slot="details">
        <a on:click="{() => active = false}" href="/book1/6-1"><Note/> Connect to Storage</a>
<a on:click="{() => active = false}" href="/book1/6-2"><Note/> Add Manifest file</a>
<a on:click="{() => active = false}" href="/book1/6-3"><Note/> Add App icons files</a>
<a on:click="{() => active = false}" href="/book1/6-4"><Note/> Service-worker.js File</a>
<a on:click="{() => active = false}" href="/book1/6-5"><Note/> Deploy to Firebase Hosting</a>
<a on:click="{() => active = false}" href="/book1/6-6"><Note/> Command errors</a>
<a on:click="{() => active = false}" href="/book1/6-7"><Note/> Deploy to Netlify</a>
<a on:click="{() => active = false}" href="/book1/6-8"><Note/> Setup Git</a>
<a on:click="{() => active = false}" href="/book1/6-9"><Note/> Don't tell me i am wrong</a>
<a on:click="{() => active = false}" href="/book1/6-10"><Note/> Don't tell me i am wrong</a>
       
    </div>
</Accordion>
<Accordion><!-- 7 -->
    <div slot="head"><span class="hn">07</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 8 -->
    <div slot="head"><span class="hn">08</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 9 -->
    <div slot="head"><span class="hn">09</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 10 -->
    <div slot="head"><span class="hn">10</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 11 -->
    <div slot="head"><span class="hn">11</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 12 -->
    <div slot="head"><span class="hn">12</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 13 -->
    <div slot="head"><span class="hn">13</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 14 -->
    <div slot="head"><span class="hn">14</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 15 -->
    <div slot="head"><span class="hn">15</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
</div>
<slot/>

<style>
.navbar {
    width: 286px;
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
    background: #ECF0F3;
    overflow: auto;
    padding-top: 12px;
}
a{
    display: flex;
    align-items: center;
    color: #9DB2AF;
    text-decoration: none;
    font-weight: 600;
    font-size: 12px;
    padding: 12px;
    border-bottom: 1px solid #e9e9e9;
    
}
.hn {
    width: 48px;    
    position: absolute;
    background: #62E190;
    top: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    left: 0;
    border-bottom-left-radius: 6px;
    border-top-left-radius: 6px;
    color:#fff;
    font-size: 21px;
    font-weight: 300;
}
@media only screen and (max-width: 600px) {
.navbar {
    display: none;
    z-index: 99999999;
    width: 100%;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.navbar.active {
    display: block!important;
}

}
.open-nav{
    position: fixed;
    right: 0;
    top: 0;
    width:36px;
    height: 36px;
    z-index: 9999999999;
    border-bottom-left-radius: 100px;
    border: none!important;
    outline:none!important;
    box-shadow: rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset, rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset, rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, rgba(0, 0, 0, 0.06) 0px 2px 1px, rgba(0, 0, 0, 0.09) 0px 4px 2px, rgba(0, 0, 0, 0.09) 0px 8px 4px, rgba(0, 0, 0, 0.09) 0px 16px 8px, rgba(0, 0, 0, 0.09) 0px 32px 16px;
}
.open-nav:focus, open-nav:active{
    outline: none;
    border: none;
}


</style>