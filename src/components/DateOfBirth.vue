<template>
  <div>
    <label for="dob">生年月日：</label>
    <input type="date" id="dob" v-model="dob" @change="calculateAge">
    <p v-if="age !== null">あなたの年齢：{{ age }}歳</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dob: null,
      age: null
    };
  },
  methods: {
    calculateAge() {
      if (this.dob) {
        const today = new Date();
        const birthDate = new Date(this.dob);
        let age = today.getFullYear() - birthDate.getFullYear();
        const monthDifference = today.getMonth() - birthDate.getMonth();

        if (monthDifference < 0 || (monthDifference === 0 && today.getDate() < birthDate.getDate())) {
          age--;
        }

        this.age = age;
      }
    }
  }
};
</script>

<style scoped>
/* 必要に応じてスタイルを追加 */
</style>
