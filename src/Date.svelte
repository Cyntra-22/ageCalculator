<script>
	import {createEventDispatcher} from 'svelte';
    let day ;
    let month ;
    let year ;
	let currentAge;

	 const dispatch = createEventDispatcher();

     function handleInput(event) {
        
		const { name, value } = event.target;
		
		if (name === 'day') {
		day = value;
		} else if (name === 'month') {
		month = value;
		} else if (name === 'year') {
		year = value;
		}
  }

	function calculation_Age() {
		const correct = validateDate();

		if (correct) {
			const birthday = new Date(`${year}-${month}-${day}`);
			const today = new Date(); 

			let ageYears = today.getFullYear() - birthday.getFullYear();
			let ageMonths = today.getMonth() - birthday.getMonth();
			let ageDays = today.getDate() - birthday.getDate();

			if (ageMonths < 0 || (ageMonths === 0 && ageDays < 0)) {
				ageYears--;
				ageMonths += 12;
			}

			if (ageDays < 0) {
				const tempDate = new Date(today.getFullYear(), today.getMonth(), 0);
				ageDays = tempDate.getDate() + ageDays;
				ageMonths--;
			}

			currentAge = {
				years: ageYears,
				months: ageMonths,
				days: ageDays
			};

			dispatch('ageCalculated', currentAge);

		}
		else{
			return null;
		}
}

  	function validateDate() {

		const dayInt = parseInt(day, 10);
		const monthInt = parseInt(month, 10);
		const yearInt = parseInt(year, 10);
    	     
		const isValidDay = dayInt >= 1 && dayInt <= 31;
		const isValidMonth = monthInt >= 1 && monthInt <= 12;
		const isValidYear = yearInt >= 1900 && yearInt <= 2100; 

		return isValidDay && isValidMonth && isValidYear;
  }

  
</script>

<style>
    .date-container{
        display: flex;
        justify-content: space-between;
        width: 80%;
    }

    input{
        margin-top: 7px;
        width: 90px;
		font-weight: bold;
		font-size: 24px;
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
		border-radius: 50%;
	}

	@media (min-width: 400px ) and (max-width: 765px){
		.date-container{
			width: 40%;
			
   	 	}
		input{	
			
			width: 70px;
			font-size: 17px;
    	}

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
			<button on:click={calculation_Age}><img src="/icon-arrow.svg" alt="logo arrow" /></button>
		</div>
</div>				
