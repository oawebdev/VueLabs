<template>
  <div class="hello">
    <NavBar
        :variant="variant"
        :type="color"
    />
    <b-container>
      <b-form class="text-justify">
        <myFormLable
            :textLength="textLength"
            :maximumLength="maximumLength"
            :lableClass="lableClass"
        />
        <my-textarea
            :maximumLength="maximumLength"
            @setTextLength="setTextLength"
        />
        <MyButton
            :isDisabled="maximumAchieved"
        ></MyButton>
      </b-form>
    </b-container>
  </div>
</template>

<script>
import MyFormLable from '@/components/home/MyFormLable.vue'
import MyButton from '@/components/home/MyButton.vue'
import MyTextarea from '@/components/home/MyTextarea.vue'
import NavBar from '@/components/nav/NavBar.vue'

export default {
  name: 'HelloWorld',
  data: () => ({
    maximumLength: 40,
    warningLength: 30,
    textLength: 0,
    variant: "danger",
    color: "dark"
  }),
  components: {
    MyFormLable,
    MyButton,
    MyTextarea,
    NavBar
  },
  computed: {
    lableClass: function () {
      var lableClass = 'success'
      if (this.textLength >= this.maximumLength) {
        lableClass = 'danger'
      } else if (this.textLength >= this.warningLength) {
        lableClass = 'warning'
      }
      return lableClass
    },
    maximumAchieved: function () {
      return (this.textLength >= this.maximumLength)
    }
  },
  methods: {
    setTextLength (textLength) {
      this.textLength = textLength
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
