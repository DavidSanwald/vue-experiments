<template>
  <div class="bg-white overflow-hidden shadow rounded-lg h-full p-8">
    <div class="border-b border-gray-200 px-4 py-5 sm:px-6">
      Mortgage Calculator
    </div>
    <div class="px-4 py-5 sm:p-6">
      <form class="flex flex-col" @submit.prevent="checkForm">
        <p v-if="errors" class="text-red-700">{{ errors }}</p>
        <FormInput
          v-model.number="propertyPrice"
          label="Property Purchase Price"
          name="purchasePrice"
        />
        <FormInput
          v-model.number="totalSavings"
          label="Total Savings"
          class="mt-8"
          name="totalSavings"
        />
        <FormRangeInput
          v-model.number="annualRepaymentRate"
          label="Annual repayment rate (%)"
          class="mt-8"
          name="annualRepayment"
        />
        <FormCheckBox
          v-model.number="realEstateCommission"
          label="Real Estate Comission"
          class="mt-8"
          name="realestateCommission"
        />
        <div class="mt-8">
          <button
            type="submit"
            class="inline-flex items-center px-4 py-2 border border-transparent text-sm leading-5 font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-500 focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700 transition ease-in-out duration-150"
          >
            Calculate
          </button>
        </div>
      </form>

      <div class="flex mt-10">
        <FeedbackCard
          label="Implied loan"
          :value="rawLoanAmount + ' € '"
          class="w-1/2"
        />
        <FeedbackCard
          label="Loan to value"
          :value="loanToValue"
          class="w-1/2 ml-8"
        />
      </div>
    </div>
  </div>
</template>

<script>
import FormInput from "./FormInput";
import FormCheckBox from "./FormCheckBox";
import FormRangeInput from "./FormRangeInput";
import FeedbackCard from "./FeedbackCard";

const brokerTax = 0.0714;
const cityTax = 0.06;

export default {
  name: "HypoForm",
  methods: {
    checkForm: function(e) {
      console.log(e);
      this.errors = null;

      if (
        !(this.propertyPrice && this.totalSavings && this.annualRepaymentRate)
      ) {
        this.errors = "Please fill in all required fields";
      }
      if (!this.errors) {
        return true;
      }

      e.preventDefault();
    }
  },
  components: {
    FormInput,
    FormCheckBox,
    FormRangeInput,
    FeedbackCard
  },
  computed: {
    stampDutyCosts() {
      return cityTax * this.propertyPrice;
    },
    notaryCosts() {
      return 2144.0 + 0.013 * (this.propertyPrice - 100000.0);
    },
    brokerCosts() {
      return brokerTax * this.propertyPrice;
    },
    totalCost() {
      return this.notaryCosts + this.brokerCosts + this.stampDutyCosts;
    },
    rawLoanAmount() {
      return this.totalCost - this.totalSavings + this.propertyPrice;
    },
    loanToValue() {
      return this.rawLoanAmount / this.propertyPrice;
    }
  },
  data() {
    return {
      errors: null,
      propertyPrice: null,
      totalSavings: null,
      annualRepaymentRate: null,
      realEstateCommission: null
    };
  }
};
</script>
