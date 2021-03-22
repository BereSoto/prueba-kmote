<template>
 <footer class="footer bg-footer">
  <div class="content has-text-left">
    <div class="columns">
      <div class="column is-four-fifths">
        <h4 class="has-text-white ">Terminos y condiciones</h4>
        <h4 class="has-text-white ">Política de privacidad</h4>
      </div>
      <div class="column auto">
          <h4 class="has-text-white">Lorem ipsum dolor</h4>
          <div class="icon-text">
            <span class="icon has-text-info">
            <img src="~/assets/icons/facebook.svg" alt="logo_facebook">
            </span>
            <span class="has-text-white">Facebook</span>
          </div>
      <div class="icon-text">
        <span class="icon has-text-success">
          <img src="~/assets/icons/twitter.svg" alt="logo_twitter">
        </span>
        <span class="has-text-white">Twitter</span>
      </div>
      <div class="icon-text">
        <span class="icon has-text-warning">
         <img src="~/assets/icons/instagram.svg" alt="logo_instagram">
        </span>
        <span class="has-text-white">Instagram</span>
      </div>
      </div>
    </div>
  </div>
</footer>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'TheFooter',
})
</script>

<style>
.bg-footer{
background-color:#4FB1BD;
}
</style>
