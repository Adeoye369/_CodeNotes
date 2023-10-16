# Some interesting vue discovery

![Vue input and save](img/Screenshot%202023-10-16%20190559.png)

````html
    <div class="cus cus_desp" id="detail2">
                    <h1>Welcome,Babatunde</h1>
                    <textarea  cols="30" rows="5" v-bind:value="content" v-on:input="setTextContent"></textarea>
                   <hr>
                    <button v-on:click="resetInput" class="btn">Reset Input</button>
                    <p>{{saveContent}}</p>

                </div>
````

This is the javascript code

```javascript
    const app1 = Vue.createApp({
  data() {
    return {
      content: "",
      saveContent: "",
      midContent: "",
    };
  },

  methods: {
    setTextContent(event) {
      // get value of input
      this.content = event.target.value;

      // Be updating as one is typing
      this.saveContent = this.midContent + this.content;
    },

    resetInput() {
      // before reset, save the content
      this.midContent += this.content;

      // Reset the content
      this.content = "";
    },
  },
}).mount(`#detail2`);

```
