<div>
    <slot/>
</div>
<style>
div {
    background: #F4F5F7;
    height: 100vh;
}
:global(html, body ) {
    margin: 0;    
    padding: 0!important;
}
:global(*) {
    box-sizing: border-box;
}
</style>