<script>
	import Date from "./Date.svelte";
	export let day = 20;
	export let month = 10; 
	export let year = 22;
</script>


<style>
	:root{
		--font-color: hsl(259, 100%, 65%);
		--font: 'Poppins', sans-serif;
		--bgColor:  hsl(0, 0%, 86%);
		--lineColor: hsl(0, 1%, 44%);
	}

	:global(body){
		padding: 0;
		margin: 0;
		font-family: var(--font); 
		background-color: var(--bgColor);  	 
	}


	.main-container{
		
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%,-50%);
		background-color: hsl(0, 0%, 100%);
		padding: 20px;
		width: 30%;
		box-shadow: 0 6px 6px rgba(0, 0, 0, 0.1);
		border-radius: 10px 10px 100px 10px;
	
	}
	.date-conponent{
		width: 70%;
		padding-left: 25px;
	}

	.line-container{
		display: flex;
		align-items: center;
		width: 90%;
	}

	.line{
		flex: 1;
		border-top: 1px solid hsl(0, 0%, 86%);
		
	}

	.img-style {
		background-color: var(--font-color);
		border-radius: 50%;
		cursor: pointer;
		width: 60px;
		height: 60px;
	}

	img{
		width: 50px;
		height: 25px;
		padding-top: 12px;
	}

	.img-style:hover{
		background-color: black;
	}

	.center-container{
		display: flex;
		flex-direction: column;
		align-items: center; 
	}
	.year-calculation{
		padding-left: 19px;
		font-size: 60px;
		font-weight: 1000;
	}

	.date-style{
		color: var(--font-color);
		background-color: none;
	}

	button{
		border: none;
		background-color: transparent;
	}

</style>

<main>
	<div class="main-container">

			<div class="date-conponent">
					<Date  />
			</div>
			<div class="center-container">
				<div class="line-container">
					<div class="line"></div>
					<div class="img-style">
						<button><img src="/icon-arrow.svg" alt="logo arrow" /></button>
					</div>
				</div>				
			</div>
			<div class="year-calculation">
				<span class="date-style">{year}</span><i>years</i>
				<span class="date-style">{month}</span><i>months</i>
				<span class="date-style">{day}</span><i>days</i>
			</div>
					
	</div>
</main>
