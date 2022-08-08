<script>

    export let qrLink;

    let src=`https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=${qrLink}`

</script>

<main>

    <img src="{src}" alt="{qrLink}">
</main>