<script>
     let day;
     let month ;
     let year;

     
    
</script>

<style>
    .date-container{
        display: flex;
        justify-content: space-between;
        width: 75%;
    }

    input{
        margin-top: 7px;
        width: 80px;
    }

    .line-container{
		display: flex;
		align-items: center;
	}

	.line{
        width: 100%;
		border-bottom: 1px solid hsl(0, 0%, 86%);
		
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

    button{
		border: none;
		background-color: transparent;
	}
</style>

<div class="date-container">
    <div>
        <label for="dayInput">DAY</label>
        <input type="number" placeholder = "DD" bind:value={day}/>
    </div>
    <div>
        <label for="dayInput">MONTH</label>
        <input type="number" placeholder = "MM" bind:value={month}/>
    </div>
    <div>
        <label for="dayInput">YEAR</label>
        <input type="number" placeholder = "YY" bind:value ={year}/>
    </div>
</div>

<div class="line-container">
	<div class="line"></div>
		<div class="img-style">
			<button ><img src="/icon-arrow.svg" alt="logo arrow" /></button>
		</div>
</div>				
