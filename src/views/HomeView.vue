<template>
  <v-container class="d-flex">
    <v-card color="#90CAF9"
      class="mx-auto my-15 "
      width="min(90%, 25rem)"
      min-height="350"
    >
    <v-card-title class="">Whilmer Realigue </v-card-title>
    <v-card-subtitle>Exam 3</v-card-subtitle>
      <v-container>
        <v-form @submit.prevent="calculate">
          <v-text-field
            label="loan"
            placeholder="loan"
            dense
            solo
            v-model="loan"
          ></v-text-field>
          <v-text-field
            label="interest"
            placeholder="interest"
            dense
            solo
            v-model="interest"
          ></v-text-field>
          <v-text-field
            label="months"
            placeholder="months"
            dense
            solo
            v-model="months"
          ></v-text-field>
          <v-btn color="primary" type="submit" small block>Calculate</v-btn>
        </v-form>
      </v-container>
      <v-container class="text-center" v-if="monthlyInstallment">
        <span class="font-bold" >Monthly Installment:</span>
        <p class="font-weight-medium">{{ monthlyInstallment }}</p>
      </v-container>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "Home",

  components: {},
  data: () => ({
    loan: 100000,
    interest: 3.5,
    months: 12,
    monthlyInstallment: null,
  }),
  methods: {
    calculate() {
      const interestRate = this.interest / 100 / 12;
      const numerator = interestRate * this.loan;
      const denominator = 1 - Math.pow(1 + interestRate, -this.months);

      const monthlyInstallment = (numerator / denominator).toFixed(2);
      this.monthlyInstallment = `${monthlyInstallment}`;
    },
  },
};
</script>

