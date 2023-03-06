<script setup></script>

<template>
  <form>
    <legend>Formatted Data Selection Controls</legend>
    <fieldset>
      <div class="row">
        <div class="col-auto">
          <label for="start-date" class="form-label">Enter date:</label
          ><input
            id="start-date"
            class="form-control"
            type="date"
            name="start-date"
            min="2023-01-01"
            max="2023-12-31"
          />
        </div>
        <div class="col-auto">
          <label for="start-time" class="form-label">Enter time:</label
          ><input
            id="start-time"
            class="form-control"
            type="time"
            name="start-time"
            min="9:00"
            max="17:00"
          />
        </div>
        <div class="col-auto">
          <label for="start-date-time" class="form-label">Enter date and time:</label
          ><input
            id="start-date-time"
            class="form-control"
            type="datetime-local"
            name="start-date-time"
            min="2023-01-01T9:00"
            max="2023-12-31T17:00"
          />
        </div>
      </div>
      <div class="row">
        <div class="col-auto">
          <label for="color" class="form-label">Choose color:</label
          ><input
            id="color"
            class="form-control form-control-color"
            type="color"
            name="color"
          />
        </div>
        <div class="col-auto">
          <label for="pic" class="form-label">Choose picture:</label
          ><input
            id="pic"
            class="form-control"
            type="file"
            name="profile-pic"
            accept="image/png, image/jpeg"
          />
        </div>
        <div class="col-auto">
          <label for="password" class="form-label">Enter password:</label
          ><input
            id="password"
            class="form-control"
            type="password"
            name="password"
            minlength="8"
            required
          />
        </div>
      </div>
    </fieldset>
  </form>
</template>
