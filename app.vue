<script setup lang="ts">
import {Gender, Popularity,Length, names} from "@/data"

interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length
}

  const options = reactive<OptionsState>({
    gender: Gender.GIRL,
    popularity: Popularity.TRENDY,
    length: Length.SHORT
  })

  const computeSelectedNames =() => {
    const filteredNames = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) =>{
      if (options.length === Length.ALL) return true
      else return name.length = options.length
    })
    selectedNames.value = filteredNames.map((name) => name.name)
  };

  const selectedNames =ref<string[]>([]);

  const optionsArray = [
    {
      title: "1) Choose a gender",
      category: "gender",
      buttons: [Gender.GIRL, Gender.UNISEX, Gender.BOY]
    },
    {
      title: "2) Choose the name's popularity",
      category: "popularity",
      buttons: [Popularity.TRENDY, Popularity.UNIQUE]
    },
    {
      title: "3) Choose the name's length",
      category: "length",
      buttons: [Length.ALL, Length.LONG, Length.SHORT]
    },
  ]

</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click  the "Find Names" button below</p>
    <div class="options-container">
      <Option 
      v-for="option in optionsArray" 
      :key="option.title" 
      :option="option"
      :options="options"
      />
        <button class="primary" @click="computeSelectedNames">Find names</button>
    </div>
    <div class="cards-container">
      <div v-for="name in selectedNames" :key="name" class="card">
          <h4>{{ name }}</h4>
        <p>x</p>
      </div>
    </div>
    
  </div>
</template>

<style scoped>
  .container{
    font-family: Arial, Helvetica, sans-serif;
    color: rgb(27,60,138);
    max-width: 50rem;
    margin: 0 auto;
    text-align: center;
  }
  h1 {
    font-size: 3rem;
  }

  

.primary {
  background-color: rgb(249,87,89);;
  color:white;
  border: none;
  border-radius: 6.5rem;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container{
  display: flex;
  margin-top: 5rem;
  flex-wrap: wrap;
}

.card{
  background-color: rgb(27,60,138);
  width: 29%;
  color:rgb(221, 229, 236);
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
  position: relative;
}

.card p{
  position: absolute;
  top: -30%;
  left: 93%;
  cursor: pointer;
  color: rgba(255,255,255,0.178)
}
</style>



