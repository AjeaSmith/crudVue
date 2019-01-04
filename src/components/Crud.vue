<template>
  <div>
    <section class="content">
      <div class="content-container">
        <div class="content-inner">
          <div class="content-header">
            <h3>
              Book Titles
              <span class="js">Vuejs</span>
            </h3>
          </div>
          <div class="content-body">
            <ul class="book-titles">
              <li v-for="(book, index) in booklist" :key="index">
                <span>{{book.title}}</span>
                <button v-on:click="deleteItem(index)" type="submit" class="delete">Delete</button>
              </li>
            </ul>
          </div>
          <div class="content-form">
            <form id="form" v-on:submit.prevent>
              <input
                v-model="booktext"
                type="text"
                placeholder="Enter a Book Title"
                class="text-field"
              >
              <input type="submit" value="Add" class="submit-field" v-on:click="add">
            </form>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "crud",
  data() {
    return {
      booktext: "",
      booklist: [],
      id: 0
    };
  },
  methods: {
    add() {
      this.booktext == ""
        ? "return"
        : this.booklist.push({
            id: this.id++,
            title: this.booktext
          });
      this.booktext = "";
    },
    deleteItem(index) {
      this.booklist.splice(index, 1);
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  width: 100%;
  height: 100%;
  font-family: "Source Sans Pro", sans-serif;
}

.content {
  width: 100%;
  height: 100vh;
}
.content .content-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.content .content-inner {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
@media (min-width: 500px) {
  .content .content-inner {
    max-width: 480px;
    height: 620px;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: pink;
    border: 2px solid #d7d7d7;
  }
}
.content .content-header {
  font-size: 1.6em;
  color: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #d35454;
  height: 60px;
}
.content .content-header .js {
  color: #487ebc;
}
.content .content-body {
  margin-top: 30px;
  height: auto;
  display: flex;
  align-items: flex-start;
}
@media (min-width: 768px) {
  .content .content-body {
    width: 100%;
  }
}
.content .book-titles {
  width: 100%;
  list-style: none;
}
.content li {
  justify-content: space-between;
  align-items: center;
  display: flex;
  border-left: 7px solid #d35454;
  color: #343434;
  margin: 15px;
  padding: 11px;
  background: #ededed;
  text-transform: capitalize;
}
.content li button {
  float: right;
  background: #d35454;
  border: none;
  color: #ffffff;
  padding: 8px;
}
.content li button:first-letter {
  text-transform: capitalize;
}
.content li button:focus-visible {
  outline: none;
}
.content .content-form form {
  justify-content: center;
  align-items: center;
  display: flex;
  height: auto;
  flex-direction: column;
}
.content .content-form form input[type="text"] {
  border: none;
  outline: none;
  color: #868686;
  background: #dfdfdf;
}
.content .content-form form input[type="text"]:focus {
  outline: none;
}
.content .content-form form form {
  width: 80%;
}
.content .content-form form input[type="text"],
.content .content-form form input[type="submit"] {
  font-size: 0.9em;
  width: 80%;
  padding: 10px;
  margin: 10px 0;
}
.content .content-form form input[type="submit"] {
  background: #d35454;
  border: none;
  color: #ffffff;
}
.content .content-form form input[type="submit"]:focus {
  outline: none;
}
</style>