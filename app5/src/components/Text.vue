<script setup></script>

<template>
  <form>
    <legend>Arbitrary Text</legend>
    <legend>Validated Text</legend>
    <fieldset>
      <div class="row">
        <div class="col-auto">
          <label for="text" class="form-label">Text</label
          ><input id="text" class="form-control" type="text" />
        </div>
        <div class="col-auto">
          <label for="search" class="form-label">Search</label
          ><input id="search" class="form-control" type="search" />
        </div>
        <div class="col-auto">
          <label for="textarea" class="form-label">TextArea</label
          ><textarea id="textarea" class="form-control" rows="1"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-auto">
          <label for="email" class="form-label">Email</label
          ><input id="email" class="form-control" type="email" />
        </div>
        <div class="col-auto">
          <label for="phone" class="form-label">Telephone</label
          ><input id="phone" class="form-control" type="tel" />
        </div>
        <div class="col-auto">
          <label for="url" class="form-label">URL</label
          ><input id="url" class="form-control" type="url" />
        </div>
      </div>
    </fieldset>
  </form>
</template>

<style scoped></style>
