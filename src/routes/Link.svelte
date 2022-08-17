<script>
	import { Base64 } from 'js-base64';
	export let params = {};
    let data = params.d;
	let url = data.split(".")[0];
	let uploader = data.split(".")[1];
	let decrypted_url = Base64.decode(url);
	let domain = decrypted_url.split("/")[2];


	function redirect() {
		window.location.href = decrypted_url;
	}
</script>

<main>
	<div class="container d-flex justify-content-center text-center">
	<div class="container ">
	{#if data.includes(".") && uploader.length > 0 }
		<h3>Link fornito da <b>{Base64.decode(uploader)}</b></h3>
		{:else}
		<h3>Link fornito da <b>GABG<b></h3>
	{/if}
	<a href="{decrypted_url}"><button class="btn btn-primary btn-lg"><i class="bi bi-link-45deg"></i> Portami a destinazione</button></a>
	<br>
	<small>Questo link ti porterà verso <b>{domain}</b></small>
</div>
</div>
</main>
