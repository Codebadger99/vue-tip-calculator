<template>
	<div class="container">
		<img src="../assets/images/logo.svg">

<div class="card">
	    <div class="container2">
	    	<div class="component-1">
	    		<div class="bill-input">
	    			<h3>bill</h3>
	    			<input type="text" name="amount" class="bill"  placeholder="0" v-model="amount">
	    		</div>

	    		<div class="select-tip">
	    			<h3>select tip %</h3>
	    			<div class="tip-card">
	    				
	    		<button class="card-tip" @click="handleClick(5)" :class="{active: activeBtn}">
	    			5$
	    		</button>
	    		<button class="card-tip"  @click="handleClick(10)" :class="{active: activeBtn}">
	    			10$
	    		</button>
	    		<button class="card-tip"  @click="handleClick(15)" :class="{active: activeBtn}">
	    			15$
	    		</button>
	    		<button class="card-tip"  @click="handleClick(25)" :class="{active: activeBtn}">
	    			25$
	    		</button>
	    		<button class="card-tip"  @click="handleClick(50)" :class="{active: activeBtn}">
	    			50$
	    		</button>
	    		<input type="text" class="card-tip card-tip-input" placeholder="custom" v-model="input">
	    			</div>
              

	    		</div>
	    		<div class="people">
	    		<h4>number of people</h4>
	    		<input type="text" name="people" class="people2" placeholder="0" v-model="people">
	    	</div>

	    	</div>
	    	
	    		
	    	<div class="component-2">
	    			<div class="amountCard">
	    		<div class="TipAmount">
	    			<h3>Tip Amount
<p>/person</p>
	    			</h3>
	    			
	    			<h1>
	    				<img src="../assets/images/icon-dollar.svg" class="img">
	    				0.00
	    			</h1>
	    		</div>
	    		<div class="TipTotal">
	    			<h3>Total
	    			<p>/person</p></h3>
	    			
	    			<h1>
	    				<img src="../assets/images/icon-dollar.svg" class="img">
	    				0.00
	    			</h1>
	    		</div>
	    		<div class="button">
	    			<button class="reset">RESET</button>
	    		</div>
	    	</div>
	    	
	    		
	    	</div>
	    	</div>
	    	
	  
	    </div>
	</div>
	

</template>

<script>
import { ref, computed } from 'vue'
export default {

  name: 'TipCalc',
 setup(){
 	const amount = ref('')
  const tips = ref([50, 10, 15, 20, 50])
  const input = ref('')
  const people = ref('')
  const activeBtn = ref(false)
 
  const handleClick = (num) => {
  	if(num){
  		!activeBtn.value
  	} 
  	input.value = num
  }

 	return { handleClick, input, amount, people, activeBtn }
 }
}
</script>

<style src="./tipCalc.css"></style>