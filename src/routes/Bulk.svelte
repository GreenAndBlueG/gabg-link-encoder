<script>
    import { Base64 } from "js-base64";
    let data = [];
    let uploader = "";
    function generateLinks() {
        data = []
        document.getElementById("links").value = "";
        let links = document.getElementById("encode").value.split("\n");
        links.forEach((link) => {
            let b64link;
            if (link.length > 0) {
                if(uploader != ""){
                    b64link = "https://link-encoder.gabg.site/#/link/" + Base64.encodeURI(link, {urlsafe: true,}) + '.' + Base64.encodeURI(uploader, {urlsafe: true,});
                }else{
                    b64link = "https://link-encoder.gabg.site/#/link/" + Base64.encodeURI(link, {urlsafe: true,});
                }
                data.push(b64link);
            }
        });
         data.forEach((link) => {
            document.getElementById("links").value += link + "\n";
        });
    }
</script>

<main>
    <div class="d-flex justify-content-center text-center">
    <div class="container">
        <h1>GABG Bulk Link Encoder</h1>
    <textarea
        placeholder="Inserisci i link (un link per linea!)"
        class="form-control"
        id="encode"
    />
    <input
        bind:value={uploader}
        placeholder="Fornitore (facoltativo, valore predefinito: GABG)"
        class="form-control"
        id="encode"
    />
    <textarea
        class="form-control"
        id="links"
        placeholder="Link codificati in Base64"
        readonly
    />
    <a href="/#/">Condificatore di link singoli</a>
    <br>
    <button class="btn btn-lg btn-primary" on:click={generateLinks}>Codifica!</button>
</div>
</div>
</main>

<style>
</style>
