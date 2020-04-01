// import users from '@src/data/data.json'

Vue.component('app-header', {
  template: "<div><h1>Component Title</h1></div>"
});

Vue.component('app-footer', {
  template: '<div><h4>testdriven.io (2019)</h4></div>'
});

var view_model = new Vue({
  el: '#vue_app',
  data: {
    navTitle: "Vue CRUD",
    footerMessage: "textDriven.io (2019)",
    // return {
    //   users:user
    // }
    users: [
      'Fred',
      'Barney',
      'Wilma',
      'Betty',
      'Dino',
      'Mr. Slate',
    ],
    usersTextColor: [
      'white',
      'white',
      'white',
      'white',
      'white',
      'white',
    ],
    newUser: "",
    displayUsers: false,
    searchName: "",
  },
  methods: {
    changeDisplay() {
      this.displayUsers = !this.displayUsers;
    },
    addNewUser(newUserInput) {
      if (newUserInput !== '') {
        this.users.push(newUserInput);
        this.newUser = "";

        for (var i = 0; i < this.usersTextColor.length; i++) {
          this.usersTextColor[i] = 'white';
        }
        this.usersTextColor.push('darkgreen');
      }
    },
  },
  computed: {
    numberOfUsersText() {
      return "There are " + this.users.length + " users.";
    },
    searchResults() {
      if (this.searchName != "") {
        return this.users.filter(el => el.match(this.searchName))
      } else {
        return "";
      }
    },
    searchTextClass() {
      if (this.searchName != ''){
        return 'searchTitleBold'
      } else {
        return 'searchTitleNormal'
      }
    }
  }
});
