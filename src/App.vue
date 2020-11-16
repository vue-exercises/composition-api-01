<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" v-model="lastName" />
    </div>
  </section>
</template>

<script>
import { ref, computed, watch } from 'vue';

export default {
  setup() {
    let firstName = ref('');
    let lastName = ref('');
    let uAge = ref(31);

    watch(uAge, function(newValue, oldValue) {
      console.log('Old age: ' + oldValue);
      console.log('New age: ' + newValue);
    });

    let uName = computed(function() {
      return firstName.value + ' ' + lastName.value;
    });

    function setNewAge() {
      uAge.value += 1;
    }

    return {
      userName: uName,
      age: uAge,
      setAge: setNewAge,
      firstName,
      lastName
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
