<template>
	<div class="container">
		<img src="../assets/images/logo.svg">

<div class="card">
	    <div class="container2">
	    	<div class="component-1">
	    		<div class="bill-input">
	    			<h3>bill</h3>
	    			<input type="number" name="amount" class="bill"  placeholder="0">
	    		</div>

	    		<div class="select-tip">
	    			<h3>select tip %</h3>
	    			<div class="tip-card">
	    		<button class="card-tip">
	    			5$
	    		</button>
	    		<button class="card-tip">
	    			10$
	    		</button>
	    		<button class="card-tip">
	    			15$
	    		</button>
	    		<button class="card-tip">
	    			25$
	    		</button>
	    		<button class="card-tip">
	    			50$
	    		</button>
	    		<input type="number" class="card-tip card-tip-input" placeholder="custom">
	    			</div>
              

	    		</div>
	    		<div class="people">
	    		<h4>number of people</h4>
	    		<input type="number" name="people" class="people2" placeholder="0">
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
export default {

  name: 'TipCalc',
 setup(){
 	
 }
}
</script>

<style src="./tipCalc.css"></style>