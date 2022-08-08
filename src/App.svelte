<script>
  
  import QrCode from "./lib/QRCode.svelte";

  let qrLink = "";
  let isQrValid = false;
  
  function updateQr(event){
    qrLink = event.target.value.trim();
    
  }

  function generateQR(){
    ( qrLink.length !== 0 ) ? isQrValid = true : isQrValid = false;
  }

  function newQR(){
    isQrValid=false;
    qrLink=""
  }

</script>


<main>
  
  <form action="">

    <label for="qrLink">Enter the Url to generate its QR Code</label>
    <input type="url" name="qrLink" value="{qrLink}" on:input="{updateQr}">

  </form>

  <div class="btnGrp">

    <button on:click="{generateQR}">Generate QR</button>
    <button on:click="{newQR}">New QR</button>

  </div>
  

  {#if (isQrValid)}
  
  <QrCode {qrLink}/>

  {/if}

</main>


<style>

  :root{
    --inputColDarker: #2a2828;
    --inputColLighter: #373636;
    --globalTransition : 0.6s;
  }

  main,form{
    display: flex;
    flex-direction: column;
  }

  form,.btnGrp{
    margin-bottom: 30px;
  }

  main{
    padding: 50px;
    border-radius: 20px;
    background-color: var(--inputColDarker);
  }

  input,input:hover,input:focus-visible{
    outline: none;
    border: none;
  }

  input{
    position: relative;
    background: var(--inputColLighter);
    margin: 30px 0 5px 0;
    padding: 15px 15px;
    height: 20px;
    width: 105%;
    border-radius: 10px;
    transform: translateX(-8%);
    transition: var(--globalTransition);
  }

</style>
