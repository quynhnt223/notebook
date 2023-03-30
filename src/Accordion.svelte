<script>    

    export let open = false;      
      const handleClick = () => open = !open
      export function clickme()  {
        alert("hello")
    }
  </script>
  
  <div class="accordion">
      <div on:click={handleClick} class="header">
          <div class="text">
              <slot name="head"></slot>	
          </div>          
          <div class="plus"></div>
      </div>
      
      {#if open}
      <div class="details" >
          <slot name="details">
          </slot>
      </div>
      {/if}
  </div>
  
  <style>
      div.accordion {          
          position: relative;    
          margin-bottom: 12px;
          margin-left: 12px;
          margin-right: 12px;  
          background-color: #ECF0F3;
    box-shadow: 0.2rem 0.2rem 0.4rem #c8d0e7, -1px -1px 2px 0px #FFFFFFF7;
    border-top: solid 2px #fff;
    border-left: solid 2px #fff;
    border-radius: 6px;
}


              
      
      
      div.header {
          display:flex;          
          position: relative;
          padding:12px;height: auto;                 
          background: #fff;
          cursor: pointer;
          border-radius: 6px;
          padding-left: 60px;

      }
      
      div.header .text {
          flex: 1;
          margin-right: 5px;
          font-weight: 700;
          font-size: 14px;
      }
      
      div.details {
          
          padding-left: 0px;
          padding-right: 0px;
          border-radius: 0 0 6px 6px;
          background: #fff;
          padding-bottom: 12px;
          border-bottom-left-radius: 6px;
          border-bottom-right-radius: 6px;          
      }
      .plus {
    display: flex;
    align-items: center;
}
  </style>
  