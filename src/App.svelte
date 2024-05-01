<script>
	import Date from "./Date.svelte";
	export let day = '--';
	export let month = '--'; 
	export let year = '--';

	function showResult(){
		alert(day, month, year);
	}
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
		width: 85%;
		padding-left: 25px;
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

	

</style>

<main>
	<div class="main-container">

			<div class="date-conponent">
					<Date/>
			</div>
			
			<div class="year-calculation">
				<span class="date-style">{year}</span><i>years</i><br>
				<span class="date-style">{month}</span><i>months</i><br>
				<span class="date-style">{day}</span><i>days</i><br>
			</div>
					
	</div>
</main>
