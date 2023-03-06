<script setup></script>

<template>
  <form>
    <legend>Buttons</legend>
    <fieldset class="unique">
      <div class="btn-group">
        <input
          id="submit"
          class="btn btn-outline-info m-3"
          type="submit"
          value="Submit"
        /><input
          id="reset"
          class="btn btn-outline-info m-3"
          type="reset"
          value="Reset"
        /><input
          id="logout"
          class="btn btn-outline-info m-3"
          type="button"
          value="Custom"
        />
      </div>
      <input id="login" class="btn btn-outline-info m-3" type="image" src="favicon.ico" />
      <div class="btn-group">
        <button class="btn btn-outline-info m-3" type="submit">Submit</button
        ><button class="btn btn-outline-info m-3" type="reset">Reset</button
        ><button class="btn btn-outline-info m-3" type="button">Custom</button>
      </div>
    </fieldset>
  </form>
</template>
