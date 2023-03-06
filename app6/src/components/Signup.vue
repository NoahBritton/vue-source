<script setup>
import { reactive } from "vue";

const order = reactive({
  name: {
    first: "",
    last: "",
  },
  email: "",
  shirt: {
    color: "",
    size: "",
    quantity: "",
  },
  date: "",
  address: {
    street: "",
    street2: "",
    city: "",
    zip: "",
  },
});

function printData() {
  if (
    order.name.first == "" ||
    order.name.last == "" ||
    order.email == "" ||
    order.shirt.color == "" ||
    order.shirt.size == "" ||
    order.shirt.quantity == "" ||
    order.date == "" ||
    order.address.street == "" ||
    order.address.city == "" ||
    order.address.zip == ""
  ) {
    console.log("please fill in missing information");
  } else {
    console.log(JSON.parse(JSON.stringify(order)));
  }
}
</script>

<template>
  <form class="order-form m-4">
    <div class="container pt-4">
      <div class="row">
        <div class="col-12 px-4">
          <div id="form-header">
            <h1>Order Form</h1>
            <span
              >Please fill in your information and we'll be sending your order in no
              time.</span
            >
          </div>
          <hr class="mt-1" />
        </div>

        <div class="col-12">
          <div class="row mx-4">
            <div class="col-12">
              <label class="order-form-label">Name</label>
            </div>
            <div class="col-sm-6">
              <div class="form-outline">
                <input
                  type="text"
                  id="form1"
                  class="form-control order-form-input"
                  v-model="order.name.first"
                  required
                />
                <label class="form-label" for="form1">First</label>
              </div>
            </div>
            <div class="col-sm-6 mt-2 mt-sm-0">
              <div class="form-outline">
                <input
                  type="text"
                  id="form2"
                  class="form-control order-form-input"
                  v-model="order.name.last"
                  required
                />
                <label class="form-label" for="form2">Last</label>
              </div>
            </div>
          </div>

          <div class="col-12">
            <div class="row mx-4">
              <div class="col-sm-6 mt-2 mt-sm-0">
                <div class="form-outline">
                  <input
                    type="text"
                    id="form3"
                    class="form-control order-form-input"
                    v-model="order.email"
                    required
                  />
                  <label class="form-label" for="form3">Email</label>
                </div>
              </div>
            </div>
          </div>

          <div class="row mt-3 mx-4">
            <div class="col-12">
              <label class="order-form-label">T-shirt model</label>
            </div>
            <div class="col-12">
              <div class="form-check form-check-inline" required>
                <input
                  class="form-check-input"
                  name="shirtRadios"
                  type="radio"
                  id="shirtRadio1"
                  value="orange"
                  v-model="order.shirt.color"
                />
                <label class="form-check-label" for="shirtRadio1"
                  ><img src="/orange_shirt.png"
                /></label>
              </div>
              <div class="form-check form-check-inline">
                <input
                  name="shirtRadios"
                  class="form-check-input"
                  type="radio"
                  id="shirtRadio2"
                  value="purple"
                  v-model="order.shirt.color"
                />
                <label class="form-check-label" for="shirtRadio2"
                  ><img src="/purple_shirt.png"
                /></label>
              </div>
              <div class="form-check form-check-inline">
                <input
                  name="shirtRadios"
                  class="form-check-input"
                  type="radio"
                  id="shirtRadio3"
                  value="lime"
                  v-model="order.shirt.color"
                />
                <label class="form-check-label" for="shirtRadio3"
                  ><img src="/lime_shirt.png"
                /></label>
              </div>
            </div>
          </div>

          <div class="row mt-3 mx-4">
            <div class="col-12">
              <label class="order-form-label" for="inputSize">Size</label>
            </div>
            <div class="col-12">
              <div class="form-outline" data-mdb-toggle-button="false">
                <select
                  id="inputSize"
                  class="form-control"
                  v-model="order.shirt.size"
                  required
                >
                  <option value="XS" selected>XS</option>
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                  <option value="XL">XL</option>
                </select>
              </div>
            </div>
            <div class="col-12">
              <label for="" class="order-form-label">Quanitity</label>
            </div>
            <div class="col-12">
              <input
                id="number-picker"
                class="form-control"
                type="number"
                name="num"
                min="1"
                max="100"
                v-model="order.shirt.quantity"
                required
              />
            </div>
          </div>

          <div class="row mt-3 mx-4">
            <div class="col-12">
              <label class="order-form-label" for="date-picker">Date</label>
            </div>
            <div class="col-12">
              <div class="form-outline datepicker" data-mdb-toggle-button="false">
                <input
                  type="date"
                  class="form-control order-form-input"
                  id="datepicker"
                  data-mdb-toggle="datepicker"
                  v-model="order.date"
                  required
                />
                <label for="datepicker" class="form-label">Select a date</label>
              </div>
            </div>
          </div>

          <div class="row mt-3 mx-4" id="address-section">
            <div class="col-12">
              <label class="order-form-label">Adress</label>
            </div>
            <div class="col-12">
              <div class="form-outline">
                <input
                  type="text"
                  id="form5"
                  class="form-control order-form-input"
                  v-model="order.address.street"
                  required
                />
                <label class="form-label" for="form5">Street Address</label>
              </div>
            </div>
            <div class="col-12 mt-2">
              <div class="form-outline">
                <input
                  type="text"
                  id="form6"
                  class="form-control order-form-input"
                  v-model="order.address.street2"
                />
                <label class="form-label" for="form6">Street Address Line 2</label>
              </div>
            </div>
            <div class="col-sm-6 mt-2 pe-sm-2">
              <div class="form-outline">
                <input
                  type="text"
                  id="form7"
                  class="form-control order-form-input"
                  v-model="order.address.city"
                  required
                />
                <label class="form-label" for="form7">City</label>
              </div>
            </div>
            <div class="col-sm-6 mt-2 pe-sm-2">
              <div class="form-outline">
                <input
                  type="text"
                  id="form9"
                  class="form-control order-form-input"
                  v-model="order.address.zip"
                  required
                />
                <label class="form-label" for="form9">Postal / Zip Code</label>
              </div>
            </div>
          </div>

          <div class="row mt-3">
            <div class="col-12 text-right" style="display: inline-block">
              <button
                class="btn btn-primary float-end"
                type="button"
                @click="printData()"
              >
                Purchase
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </form>
  <form class="order-form m-4">
    <div class="container pt-4">
      <div class="row">
        <div class="col-12 px-4">
          <h1>Console Output</h1>
          <code class="output" style="white-space: break-spaces"></code>
        </div>
      </div>
    </div>
  </form>
</template>

<style scoped>
img {
  height: 75px;
}
.btn.btn-primary {
  background-color: green;
}
#form-header {
  padding-left: 20px;
  padding-bottom: 10px;
  background-color: green;
  border-radius: 15px 15px 0px 0px;
}
#address-section {
  background-color: rgba(0, 0, 0, 0.301);
}
</style>
