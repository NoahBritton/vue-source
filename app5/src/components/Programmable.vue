<script setup></script>

<template>
  <form>
    <legend>Programmable Selection Controls</legend>
    <fieldset>
      <div class="row">
        <div id="selectors" class="col-auto">
          <label for="selectors" class="form-check-label">Select your item(s)</label>
          <div class="form-check">
            <input
              id="item1"
              class="form-check-input"
              type="checkbox"
              name="item1"
              value="1"
            /><label for="item1">item 1</label>
          </div>
          <div class="form-check form-check-inline">
            <input
              id="item2"
              class="form-check-input"
              type="checkbox"
              name="item2"
              value="2"
            /><label for="item2">item 2</label>
          </div>
        </div>
        <div id="choices" class="col-auto">
          <label for="choices" class="form-check-label">Make a choice</label>
          <div class="form-check">
            <input
              id="choice1"
              class="form-check-input"
              type="radio"
              name="choice"
              value="a"
            /><label for="choice1">A</label>
          </div>
          <div class="form-check">
            <input
              id="choice2"
              class="form-check-input"
              type="radio"
              name="choice"
              value="b"
            /><label for="choice2">B</label>
          </div>
          <div class="form-check">
            <input
              id="choice3"
              class="form-check-input"
              type="radio"
              name="choice"
              value="c"
            /><label for="choice3">C</label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-auto">
          <label for="list-select" class="form-label">Select from the list</label
          ><input
            list="list-select"
            id="list-input"
            class="form-control"
            name="flavor"
          /><datalist id="list-select">
            <option value="1">select item 1</option>
            <option value="2">select item 2</option>
            <option value="3">select item 3</option>
            <option value="4">select item 4</option>
          </datalist>
        </div>
        <div class="col-auto">
          <label for="dropdown-select" class="form-label">Select from the dropdown</label
          ><select id="dropdown-select" class="form-select" name="cities">
            <option value="1">dropdown item 1</option>
            <option value="2">dropdown item 2</option>
            <option value="3">dropdown item 3</option>
            <option value="4">dropdown item 4</option>
          </select>
        </div>
      </div>
    </fieldset>
  </form>
</template>
