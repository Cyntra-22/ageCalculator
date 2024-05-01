<script>
     let day;
     let month ;
     let year;

     function handleInput(event) {
        const dayInt = parseInt(day, 10);
		const monthInt = parseInt(month, 10);
		const yearInt = parseInt(year, 10);
        
		const { name, value } = event.target;
		// Update the corresponding prop based on the input name
		if (name === 'day') {
		day = value;
		} else if (name === 'month') {
		month = value;
		} else if (name === 'year') {
		year = value;
		}
  }

  	function validateDate() {
    	
		

        
		const isValidDay = dayInt >= 1 && dayInt <= 31;
		const isValidMonth = monthInt >= 1 && monthInt <= 12;
		const isValidYear = yearInt >= 1900 && yearInt <= 2100; // Adjust the range as needed

		// Return true if all input values are valid, otherwise false
		return alert(isValidDay && isValidMonth && isValidYear);
  }

     
    
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
        <input type="number" placeholder = "DD" bind:value={day} on:input={handleInput}/>
    </div>
    <div>
        <label for="dayInput">MONTH</label>
        <input type="number" placeholder = "MM" bind:value={month} on:input={handleInput}/>
    </div>
    <div>
        <label for="dayInput">YEAR</label>
        <input type="number" placeholder = "YY" bind:value ={year} on:input={handleInput}/>
    </div>
</div>

<div class="line-container">
	<div class="line"></div>
		<div class="img-style">
			<button on:click={validateDate}><img src="/icon-arrow.svg" alt="logo arrow" /></button>
		</div>
</div>				
