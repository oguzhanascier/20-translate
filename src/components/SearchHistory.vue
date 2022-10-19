<template>
  <div class="well">
    <h3>Arama Geçmişi</h3>
    <ul class="list-group text-left">
      <li class="list-group-item" v-for="(h, i) in history" :key="i">
        <div>
          <strong>{{h.from}} => {{h.to}}</strong>
        </div>
        <br />
        <div>
          <strong class="text-success">{{h.translateText}}</strong>
          <span class="text-info">{{h.translatedText}}</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default{
props:['history']
}
</script>

<style></style>
