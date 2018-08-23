<template>
  <div class="LoanRequest">
		<div class="tile">
		  <h1>Loan Request</h1>
		</div>    
		<div class="field is-grouped">
		  <div class="control">
        <hr>
		    <button v-on:click="createLoanRequestPromise()" class="button is-link">Create Loan Request Promise</button>
        <hr>
        <button v-on:click="createLoanRequestAsyncAwait()" class="button is-link">Create Loan Request Async Await</button>
		  </div>
		</div>
  </div>
</template>

<script>

import Dharma  from "@dharmaprotocol/dharma.js";
const dharma = new Dharma("http://localhost:8545");
const { LoanRequest } = Dharma.Types;

const loanrequestOptions = {
           principalAmount: 5,
           principalToken: "WETH",
           collateralAmount: 100,
           collateralToken: "REP",
           interestRate: 12.3,
           termDuration: 6,
           termUnit: "months",
           debtorAddress: "0xd2f45e02ab7b190ac9a87b743eab4c8f2ed0e491",
           expiresInDuration: 5,
           expiresInUnit: "days",
}

export default {
  name: 'LoanRequest',
  methods: {
    createLoanRequestPromise: function() { 

      console.log('dharma : ', dharma);

      LoanRequest.create(dharma, loanrequestOptions).then((loanRequest) => {
          console.log(loanRequest);
      });

      //  const loanRequest = await LoanRequest.create(dharma, {
      //      principalAmount: 5,
      //      principalToken: "WETH",
      //      collateralAmount: 100,
      //      collateralToken: "REP",
      //      interestRate: 12.3,
      //      termDuration: 6,
      //      termUnit: "months",
      //      debtorAddress: "0xd2f45e02ab7b190ac9a87b743eab4c8f2ed0e491",
      //      expiresInDuration: 5,
      //      expiresInUnit: "days",
      // })

    },
    createLoanRequestAsyncAwait : function() {

      (async () => {
          const loanRequest = await LoanRequest.create(dharma, loanrequestOptions);
          console.log(loanRequest);
      })();

    }

  },
  beforeCreate () { },
  data: function () {
    return {
      count: 0
    }
  },
  created: function() { console.log('Component Created'); },
  mounted : function() { },
  computed: { }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
