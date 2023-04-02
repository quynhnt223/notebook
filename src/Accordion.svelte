<script>    
    import { afterPageLoad } from "@roxi/routify"
    export let open = false;      
      const handleClick = () => open = !open
    
  
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
@media only screen and (max-width: 600px) {
.content .accordion .details{padding: 0!important;padding-top: 12px!important;}
}
  </style>
  