<script>
	import {createEventDispatcher} from 'svelte';
    let day ;
    let month ;
    let year ;
	let currentAge;
	let dayError = '';
	let monthError = '';
	let yearError = '';

	 const dispatch = createEventDispatcher();

     function handleInput(event) {
        
		const { name, value } = event.target;
		
		if (name === 'day') {
		day = value;
		dayError = validateDay(value) ? '':'Invalid Day';
		
		} else if (name === 'month') {
		month = value;
		monthError = validateMonth(value) ? '':'Invalid Month';
		} else if (name === 'year') {
		year = value;
		yearError = validateYear(value) ? '':'Invalid Year';
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
			setTimeout(() => {
            dayError = '';
            day = '';
            monthError = '';
            month = '';
            yearError = '';
            year = '';
        }, 1500);
    }
		}

	function validateDay(day){
		const dayInt = parseInt(day,10);
		return dayInt >= 1 && dayInt <= 31;
	}

	function validateMonth(month){
		const monthInt = parseInt(month,10);
		return monthInt >= 1 && monthInt <= 12;
	}

	function validateYear(day){
		const yearInt = parseInt(year,10);
		return yearInt >= 1900 && yearInt <= 2100;
	}

  	function validateDate() {
    	     
		const isValidDay = validateDay(day);
		const isValidMonth = validateMonth(month);
		const isValidYear = validateYear(year); 

		dayError = isValidDay ? '' : 'Invalid day';
		monthError = isValidMonth ? '' : 'Invalid month';
		yearError = isValidYear ? '' : 'Invalide year';

		return isValidDay && isValidMonth && isValidYear;
  }

  function updateInputStyle() {
        if (dayError) {
            return 'border-color: red; color: red; background-color:pink;';
        } 
		else if (monthError) {
            return 'border-color: red; color: red; background-color:pink;';
        } 
		else if (yearError) {
            return 'border-color: red; color: red; background-color:pink;';
        } 		
		else {
            return '';
        }
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

	#display-line{
		display: none;
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

	button:active{
		border: none;
		background-color: transparent;
	}

	.error-style{
		color: red;
	}
	

	 @media (min-width: 300px) and (max-width: 768px ){
	
		input{			
			width: 90%;
			font-size: 15px;
			margin-bottom: 30px;
			margin-left: 15px;
    	}
		label{
			margin-left: 15px;
		}
		.line{
			width: 30%;
			
		}
		#display-line{
		display: block;
		
	}
	.error-style{
			font-size: 10px;
			margin-left: 15px;
		}
			
	}
</style>

<div class="date-container">
    <div>
        <label for="dayInput">DAY</label>
		{#if dayError}
        	<input type="number" placeholder = "DD" bind:value={day} on:input={handleInput} style="{updateInputStyle()}"/>
			<p class="error-style">{dayError}</p>
		{:else}
			<input type="number" placeholder = "DD" bind:value={day} on:input={handleInput}/>
		{/if}
    </div>
    <div>
        <label for="dayInput">MONTH</label>
		{#if monthError}
        	<input type="number" placeholder = "MM" bind:value={month} on:input={handleInput} style="{updateInputStyle()}"/>
			<p class="error-style">{monthError}</p>
		{:else}
			<input type="number" placeholder = "MM" bind:value={month} on:input={handleInput}/>
		{/if}
    </div>
    <div>
        <label for="dayInput">YEAR</label>
		{#if yearError}
        	<input type="number" placeholder = "YY" bind:value ={year} on:input={handleInput} style="{updateInputStyle()}"/>
			<p class="error-style">{yearError}</p>
		{:else}
			<input type="number" placeholder = "YY" bind:value ={year} on:input={handleInput}/>
		{/if}
    </div>
</div>

<div class="line-container">
	<div class="line"></div>
		<div class="img-style">
			<button on:click={calculation_Age}><img src="/icon-arrow.svg" alt="logo arrow" /></button>
		</div>
	<div class="line" id="display-line"></div>
</div>				
