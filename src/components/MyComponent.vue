<template>
  <div>
    <h2>Hello this is my compnent</h2>
    <hr />
    <div>
      <h2>Component data Example</h2>
      <h4>{{someMessage}}</h4>
    </div>
    <hr />
    <div>
      <h2>v-model Example</h2>
      <input v-model="enteredMessage" placeholder="Enter a message" />
      <p>Message is: {{ enteredMessage }}</p>
      <select v-model="selectedFruit">
        <option disabled value>Choose a fruit</option>
        <option>Apple</option>
        <option>Banana</option>
        <option>Strawberry</option>
      </select>
      <span>Fruit chosen: {{ selectedFruit }}</span>
      <p>Wach propery is triggered on selectedFruit Change. Watch Console log.</p>
    </div>

    <div>
      <h2>v-html Change html Example</h2>
      <select v-model="myHtmlIndex">
        <option>0</option>
        <option>1</option>
        <option>2</option>
      </select>
      <p>The below element renders HTML based on dropdown options</p>
      <div v-html="myHtml[myHtmlIndex]"></div>
    </div>
    <hr />
    <div>
      <h2>v-text Conditional</h2>
      <p>v-text with ternery js syntax. Check code</p>
      <input type="text" v-model="hiName" placeholder="Enter a HiName to Compare" />
      <input type="text" v-model="byeName" placeholder="Enter a ByeName to Compare" />
      <p v-text="hiName == byeName ? 'Names are same' : 'Names are different'"></p>
      <h3>v-if</h3>
      <p v-if="shouldShowThis">Contents in this elements are shown by executing v-if derective</p>
    </div>
    <hr />
    <div>
      <h2>v-on:eventName</h2>
      <a class="btn btn-primary" v-on:click="handleClick">Click me for OnClick event</a>
    </div>
    <hr />
    <div></div>
  </div>
</template>

<script>
export default {
  name: "MyComponent",
  props: {
    msg: String,
    username: String,
  },
  methods: {
    handleClick() {
      alert(`This is hiName ${this.byeName}`);
    },
  },
  data() {
    return {
      shouldShowThis: true,
      hiName: "",
      byeName: "",
      someMessage: "This msg is from component data",
      selectedFruit: null,
      enteredMessage: null,
      myHtml: [
        "<div><span>First template</span></div>",
        "<div><span>Second template</span></div>",
        "<div>Third Template</div>",
      ],
      items: ["car", "bike", "dog"],
      myHtmlIndex: 0,
    };
  },
  watch: {
    // This is called on selectedFruit data change
    selectedFruit: function (newValue, oldValue) {
      console.log(`New Value ${newValue},Old Value ${oldValue}`);
    },
  },
};
</script>

<style>
</style>