<script>
	import { Base64 } from 'js-base64';
	let data = '';
	let base64 = '';
	let uploader = '';
	let uploaderB64 = '';
	function getBase64(){
		base64 = Base64.encodeURI(data, {
			urlsafe: true
		});
		uploaderB64 = Base64.encodeURI(uploader, {
			urlsafe: true
		});
	}
	</script>


	<main>


	<div class="d-flex justify-content-center text-center" id="encode">
	  <div class="container">
		<h1>GABG Link Encoder</h1>
	  <input bind:value={data} on:input={() => getBase64()} placeholder="Inserisci i link da condificare" class="form-control" id="encode"/>
	  <input bind:value={uploader} on:input={() => getBase64()} placeholder="Fornitore (facoltativo, valore predefinito: GABG)" class="form-control" id="encode" />
	  {#if base64 == ''}
	  <textarea class="form-control" placeholder="Link codificato in Base64" readonly></textarea>
	  {:else if uploaderB64 == ''}
	  <textarea class="form-control" placeholder="Link codificato in Base64" readonly>https://link-encoder.gabg.site/#/link/{base64}</textarea>
	  {:else}
	  <textarea class="form-control" placeholder="Link codificato in Base64" readonly>https://link-encoder.gabg.site/#/link/{base64}.{uploaderB64}</textarea>

	  {/if}
	  <a href="/#/bulk">Codificatore di link in massa</a>
	</div>
	</div>
	</main>

	<style>

	</style>
