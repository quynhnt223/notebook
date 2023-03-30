
<script>
    import Accordion from "../../Accordion.svelte";    
    import Note from "../../components/icons/Note.svelte";
    import Content from "./Content.svelte";
    let active = true;
    import { url } from '@roxi/routify'

    
    
</script>
<div class="navbar">
<Accordion><!-- 1 -->
    <div slot="head"><span class="hn">01</span><span>Project Init</span></div>
    <div slot="details">    
        <a href="/book1/1"><Note/> Creating An App</a>
        <a href="/book1/2"><Note/> Add Manifest file</a>
        <a href="/book1/3"><Note/> Add App icons files</a>
        <a href="/book1/4"><Note/> Service-worker.js File</a>
        <a href="/book1/5"><Note/> Deploy to Firebase Hosting</a>
        <a href="/book1/6"><Note/> Command errors</a>
        <a href="/book1/7"><Note/> Deploy to Netlify</a>
        <a href="/book1/8"><Note/> Setup Git</a>
        <a href="/book1/9"><Note/> Don't tell me i am wrong</a>
        <a href="/book1/10"><Note/> Don't tell me i am wrong</a>
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
    <div slot="head"><span class="hn">04</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 5 -->
    <div slot="head"><span class="hn">05</span><span>Project Init</span></div>
	<div slot="details">

       
    </div>
</Accordion>
<Accordion><!-- 6 -->
    <div slot="head"><span class="hn">06</span><span>Project Init</span></div>
	<div slot="details">

       
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
    .navbar {display: none;z-index: 99999999;}
}
</style>