<script>
import TodoList from './components/TodoList.vue'
  export default {
    name: "App",
    data() {
        return {
            bold: "<h1>Codeshaper</h1>",
            name: "Codeshaper",
            heading: "This is cferferfr",
            active: "red",
            isDisabled: true,
            status: "underline",
            isColored: "coloring",
            styleObj: {
                color: "blue",
                fontSize: "50px",
                padding: "20px"
            },
            num: -99,
            showElement: true,
            names: ["John", "Doe", "Mike"],
            fullName: [
                { first: "John", last: "Doe" },
                { first: "Dan", last: "Brown" },
                { first: "Prison", last: "Mike" },
                { first: "Jim", last: "Halpert" },
            ],
            multiplyNum: 5
        };
    },
    methods: {
        add(a, b, c) {
            return a + b + c;
        },
        multiply(num) {
            return num * this.multiplyNum;
        }
    },
    components: { TodoList }
}
</script>

<template>
  <div>
    <TodoList/>
  </div>
</template>

<style>
.coloring {
  color: blue;
} 
.underline {
  text-decoration: underline;
}
.red {
color: red;
}
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
