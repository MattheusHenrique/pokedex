<template>
<div>
    <div class="card">
        <img style="height:auto;" width="125" height="125" :src="pokemon.sprites.front_default">
         <div class="container">
             <p>Name: {{ pokemon.name }}</p>
             <p>ID: {{ pokemon.id }}</p>
         </div>
    </div>
</div>
</template>

<script>
export default {
   props: ["pokemon"],

}
</script>

<style>

.card {

  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  margin-left: 25%;
  margin-right: 25%;
  background-color: white;
}


.card:hover {
  box-shadow: 0 16px 32px 0 rgba(0,0,0,0.2);
}


.container {
  padding: 2px 5px;
}

</style>