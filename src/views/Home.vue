<template>
<div class="home" >
  <div @click="reroll()" v-if='renderCheck(mealInfo.idMeal) == true'>
    <button>Reroll</button>
  </div>
  <div>
    <h1><a :href="mealInfo.strYoutube">{{mealInfo.strMeal}}</a></h1>
    <h3>{{mealInfo.strCategory}}, {{mealInfo.strArea}} meal</h3>
    <h4>{{mealInfo.strTags}}</h4>
    <div class="imgWrap">
      <a :href="mealInfo.strYoutube"><img :src="mealInfo.strMealThumb" alt="foodPic"></a>
    </div>
    <div class="flex-container">
      <div class="flex-section1">
        <ul>
          <li v-if='renderCheck(mealInfo.strIngredient1) == true'><b>{{mealInfo.strMeasure1}}</b> {{mealInfo.strIngredient1}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient2) == true'><b>{{mealInfo.strMeasure2}}</b> {{mealInfo.strIngredient2}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient3) == true'><b>{{mealInfo.strMeasure3}}</b> {{mealInfo.strIngredient3}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient4) == true'><b>{{mealInfo.strMeasure4}}</b> {{mealInfo.strIngredient4}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient5) == true'><b>{{mealInfo.strMeasure5}}</b> {{mealInfo.strIngredient5}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient6) == true'><b>{{mealInfo.strMeasure6}}</b> {{mealInfo.strIngredient6}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient7) == true'><b>{{mealInfo.strMeasure7}}</b> {{mealInfo.strIngredient7}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient8) == true'><b>{{mealInfo.strMeasure8}}</b> {{mealInfo.strIngredient8}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient9) == true'><b>{{mealInfo.strMeasure9}}</b> {{mealInfo.strIngredient9}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient1O) == true'><b>{{mealInfo.strMeasure10}}</b> {{mealInfo.strIngredient10}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient11) == true'><b>{{mealInfo.strMeasure11}}</b> {{mealInfo.strIngredient11}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient12) == true'><b>{{mealInfo.strMeasure12}}</b> {{mealInfo.strIngredient12}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient13) == true'><b>{{mealInfo.strMeasure13}}</b> {{mealInfo.strIngredient13}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient14) == true'><b>{{mealInfo.strMeasure14}}</b> {{mealInfo.strIngredient14}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient15) == true'><b>{{mealInfo.strMeasure15}}</b> {{mealInfo.strIngredient15}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient16) == true'><b>{{mealInfo.strMeasure16}}</b> {{mealInfo.strIngredient16}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient17) == true'><b>{{mealInfo.strMeasure17}}</b> {{mealInfo.strIngredient17}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient18) == true'><b>{{mealInfo.strMeasure18}}</b> {{mealInfo.strIngredient18}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient19) == true'><b>{{mealInfo.strMeasure19}}</b> {{mealInfo.strIngredient19}}</li>
          <li v-if='renderCheck(mealInfo.strIngredient20) == true'><b>{{mealInfo.strMeasure20}}</b> {{mealInfo.strIngredient20}}</li>
        </ul>
      </div>
      <div class="flex-section2">
        <h2 class="Instructions">Instructions</h2>
        <p>
          {{mealInfo.strInstructions}}
        </p>
      </div>
    </div>
    <a :href="mealInfo.strSource"><h2 class="Source">Source</h2></a>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
import {ref} from 'vue'

export default {
  name: 'Home',
  components: {
  },
  setup(){
    const mealInfo = ref([])
    const reroll = () => {
      fetch('https://www.themealdb.com/api/json/v1/1/random.php')
      .then(response => response.json())
      .then(data => {
        mealInfo.value = data.meals[0]
      })
    }
    const renderCheck = (ingredient) => {
      if (ingredient != "" && ingredient != null){
        return true
      }
      else{
        return false
      }
    } 
    fetch('https://www.themealdb.com/api/json/v1/1/random.php')
      .then(response => response.json())
      .then(data => {
        mealInfo.value = data.meals[0]
      })
    return {
      reroll,
      mealInfo,
      renderCheck
    }
  }
}
</script>

<style scoped>
*{
  overflow: hidden;
}
.home{
  background-color:rgb(186, 186, 202);
  border-radius:1%;
  width:60%;

  margin:auto;
}
.imgWrap{
  padding:7.5%;
  margin: -7.5% 0;
}
img{
  width:100%;
  height:100%;
  transition:all 1.5s;
  transform:scale(1);
  border-radius:1%;
  box-shadow: rgba(6, 24, 44, 0.4) 0px 0px 0px 2px, rgba(6, 24, 44, 0.65) 0px 4px 6px -1px, rgba(255, 255, 255, 0.08) 0px 1px 0px inset; 
}
img:hover,
img:focus{
  transition:all .5s;
  transform:scale(1.01);
}
button{
  margin-top:10px;
}
a{
  text-decoration: none;
  color:black;
  transition:all .5s;
}
a:hover,
a:focus{
  color:rgb(122, 125, 126);
  transition:all .5s;
}
h1{
  transform:scale(1);
  transition:all .5s; 
  background-color:rgb(213, 226, 250)
}
.Source{
  transform:scale(1);
  transition:all .5s; 
}
.Source:focus,
.Source:hover{
  transform:scale(1.04);
  transition:all .5s;
}
h1:focus,
h1:hover{
  transform:scale(1.02);
  transition:all .5s;
}
.Instructions{
  text-align:center;
}
.flex-container{
  display:flex;
  align-items: center;
  flex-direction: column;
}
.flex-section1{

  text-align:left;
  flex-grow:5;
}
ul {
    list-style-type: none;
}
.flex-section2{
  flex-grow:12;
  text-align:left;
  font-size: 1em;
  margin:0 2.5%;
}
</style>
