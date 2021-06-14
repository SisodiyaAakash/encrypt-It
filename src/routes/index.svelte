<script>
	var password="Password";
	var length = 1;

	var num = true;
	var ucase = false;
	var lcase = false;
	var symbols = false;
	
	function generatePass(){
		if(num === true && ucase === false && lcase === false && symbols === false){
			var expont = Math.pow(10, length);
			let num = Math.floor(Math.random() * expont);
			password = BigInt(num).toString();
		}
	}

	function copyClipboard(){
		const copied = document.getElementById('clipboard');
		copied.select();
		// navigator.clipboard.readText().then(clipText => document.getElementById('clipboard').innerText += clipText);
	}
</script>

<style>
	.home{
		width: 100%;
	}
	.title{
		font-size: calc(24px + 0.4vw);
	}
	.rand-pass{
		display: flex;
		flex-wrap: wrap;
		justify-content: space-evenly;
		padding: 5rem 0;
	}
	.img img{
		width: 450px;
	}
	.rand-gen{
		display: flex;
		flex-wrap: wrap;
		flex-direction: column;
	}
	.pass-disp{
		width: 350px;
		padding: 2px;
		font-size: calc(15px + 0.4vw);
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-between;
		border: 1px solid #cccccc;
		border-radius: 50px;
	}
	.pass-disp .password{
		max-width: 80%;
		margin-left: 1rem;
		overflow-x: scroll;
		border: none;
		outline: none;
		font-size: calc(16px + 0.4vw);
	}
	.pass-disp .password::-webkit-scrollbar {
		display: none;
	}
	.pass-disp svg{
		width: 20px;
		fill: #adadad;
		padding: 8px 12px;
		border-radius: 25px;
	}
	.pass-disp svg:hover{
		cursor: pointer;
		fill: #ffffff;
		background-color: #4333FF;
	}
	.copy-btn svg{
		width: 16px;
		margin-right: 0.5rem;
	}
	.copy-btn{
		display: flex;
		justify-content: center;
		align-items: center;
		cursor: pointer;
		padding: 0.5rem 1rem;
		background-color: #4333FF;
		color: #ffffff;
		border: 1px solid #4333FF;
		border-radius: 25px;
		margin-top: 1rem;
		margin-bottom: 1rem;
		margin-left: auto;
		margin-right: auto;
	}
	.copy-btn:hover{
		background-color: transparent;
		color: #4333FF;
	}

	.length-container{
		margin: 1rem 0;
		display: flex;
		align-items: center;
	}
	.length-container label{
		margin-right: 0.5rem;
	}
	.length-container input[type="range"]{
		width: 100%;
	}

	.filter-container{
		display: flex;
		flex-direction: column;
	}
	.filter{
		display: flex;
		align-items: center;
	}
	.filter .controller{
		margin-right: 1rem;
	}
	.controller, .label{
		font-size: calc(15px + 0.4vw);
	}
</style>

<svelte:head>
	<title>Encrypt It | Powered by Developar</title>
</svelte:head>

<div class="home">
	<h1 class="title">Password generator</h1>
	<div class="rand-pass">
		<div class="img">
			<img src="auth.svg" alt="Authentication">
		</div>
		<div class="rand-gen">
			<div class="pass-disp">
				<input type="text" value="{password}" id="clipboard" class="password" readonly/>
				<svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="icon svelte-1iahds4" viewBox="0 0 16 16"><path d="M11.534 7h3.932a.25.25 0 0 1 .192.41l-1.966 2.36a.25.25 0 0 1-.384 0l-1.966-2.36a.25.25 0 0 1 .192-.41zm-11 2h3.932a.25.25 0 0 0 .192-.41L2.692 6.23a.25.25 0 0 0-.384 0L.342 8.59A.25.25 0 0 0 .534 9z"></path><path fill-rule="evenodd" d="M8 3c-1.552 0-2.94.707-3.857 1.818a.5.5 0 1 1-.771-.636A6.002 6.002 0 0 1 13.917 7H12.9A5.002 5.002 0 0 0 8 3zM3.1 9a5.002 5.002 0 0 0 8.757 2.182.5.5 0 1 1 .771.636A6.002 6.002 0 0 1 2.083 9H3.1z"></path></svg>
			</div>
			<button class="copy-btn" on:click={copyClipboard}>
				<svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="icon" viewBox="0 0 16 16"><path d="M4 1.5H3a2 2 0 0 0-2 2V14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V3.5a2 2 0 0 0-2-2h-1v1h1a1 1 0 0 1 1 1V14a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V3.5a1 1 0 0 1 1-1h1v-1z"></path><path d="M9.5 1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-3a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5h3zm-3-1A1.5 1.5 0 0 0 5 1.5v1A1.5 1.5 0 0 0 6.5 4h3A1.5 1.5 0 0 0 11 2.5v-1A1.5 1.5 0 0 0 9.5 0h-3z"></path></svg>
				Copy to clipboard
			</button>
			<div class="input-container">
				<div class="input- length-container">
					<label aria-label="Slider Label" for="app-slider-8199492" class="app-slider-label"><small>{length}</small></label>
					<input type="range" bind:value={length} on:input={generatePass} title="Change Password Length" class="app-slider-input" min="1" max="50" aria-label="Slider Input">
				</div>

				<div class="filter-container">
					<label class="filter">
						<input type="checkbox" checked={num} on:input={num = !num} class="controller" />
						<span class="label">Numbers</span>
					</label>
					<label class="filter">
						<input type="checkbox" checked={ucase} on:input={ucase = !ucase} class="controller" />
						<span class="label">Uppercase</span>
					</label>
					<label class="filter">
						<input type="checkbox" checked={lcase} on:input={lcase = !lcase} class="controller" />
						<span class="label">Lowercase</span>
					</label>
					<label class="filter">
						<input type="checkbox" checked={symbols} on:input={symbols = !symbols} class="controller" />
						<span class="label">Special Characters</span>
					</label>
				</div>
			</div>
		</div>
	</div>
</div>