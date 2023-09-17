<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <p>{{ text1 }}</p>
  <p>{{ text2 }}</p>
  <p>{{ name }}</p>
  <p>{{ surn }}</p>

  <img :src="attr">
  <a :href="href">page</a>

  {{ var1 + var2 }}
  {{ num }}
  {{ arr[0] }}
  {{ obj.a }}

  <button @click="show">alert !</button>
  <button @click="show2">alert page</button>
  <button @click="show3">alert UpperCase 1 letter</button>
  <button @click="show4('text1')">show text in btn</button>

  {{ text3 }}

  <button @click="change">text</button>

  <p>{{ name }}</p>
  <p>{{ surn }}</p>
  <p>{{ full }}</p>

  <button @click="hide">hide</button>
  <button @click="toggle">{{ visible ? 'hide' : 'show' }}</button>
  <p v-if="visible">visible</p>
  <p v-if="!visible">!visible</p>

  <p v-if="isAuth">+++</p>
  <p v-else>---</p>

  <p v-if="num2 === 1 || num2 === 3">
    one or two
  </p>

  <p v-if="num == 1">one</p>
  <p v-else-if="num == 2">two</p>
  <p v-else-if="num == 3">three</p>
  <p v-else>error</p>

  <template v-if="isAuth">
    <p>+++</p>
    <p>+++</p>
    <p>+++</p>
  </template>

  <p v-show="isAuth">
    +++
  </p>

  <p v-for="elem in arr">{{ elem }}</p>

  <p v-for="(elem, key) in arr">
    {{ key }} {{ elem }}
  </p>
  <p v-for="(elem, key) in arr">
    {{ key + 1 }} {{ elem }}
  </p>

  <p v-for="(elem, key, index) in obj">
    {{ index }}
    {{ key }}
    {{ elem }}
  </p>

  <template v-for="elem in arr">
    <p>{{ elem }}</p>
    <hr>
  </template>

  <p v-for="user in users">
    {{ user.name }}
    {{ user.surn }}
  </p>

  <p v-for="num in 10">
    {{ num }}
  </p>

  <ul>
    <template v-for="elem in arr2">
      <li v-if="elem % 2 === 0">
        {{ elem }}
      </li>
    </template>
  </ul>

  <p v-for="user in users2" :key="user.id">
    {{ user.name }}
    {{ user.surn }}
  </p>

  <p v-for="elem in arr2">
    {{ elem }}
  </p>
  <button @click="add">add</button>

  <p :class="str">text</p>s

  <p :class="obj2">text</p>

  <button @click="setDone">hide</button>
  <p :class="styles">text</p>
</template>

<script>
export default {
  data() {
    return {
      text1: '111',
      text2: '222',
      name: 'john',
      surn: 'smit',
      attr: 'img.png',
      text: 'page',
      href: 'page.html',
      var1: 1,
      var2: 2,
      num: 5,
      arr: [1, 2, 3],
      obj: {a: 1, b: 2, c: 3},
      text3: 'xxx',
      visible: true,
      isAuth: true, // тут или true, или false,
      num2: 3, // пусть сейчас там 3
      users: [
        {
          name: 'name1',
          surn: 'surn1',
        },
        {
          name: 'name2',
          surn: 'surn2',
        },
        {
          name: 'name3',
          surn: 'surn3',
        },
      ],
      arr2: [1, 2, 3, 4, 5],
      users2: [
        {
          id: 1,
          name: 'name1',
          surn: 'surn1',
        },
        {
          id: 2,
          name: 'name2',
          surn: 'surn2',
        },
        {
          id: 3,
          name: 'name3',
          surn: 'surn3',
        },
      ],
      str: 'active valid',
      obj2: {
        active: true,
        valid:  false,
      },
      styles: {
        done: false,
      },
    }
  },
  methods: {
    show: function() {
      alert('!');
    },
    show2: function() {
      alert(this.text);
    },
    show3: function() {
      let text = this.cape(this.text);
      alert(text);
    },
    cape: function(str) {
      return str[0].toUpperCase() + str.slice(1);
    },
    show4: function(str) {
      alert(str);
    },
    change: function() {
      this.text3 = 'yyy';
    },
    hide: function() {
      this.visible = false;
    },
    toggle: function() {
      this.visible = !this.visible;
    },
    add: function() {
      this.arr2.push('xxx');
    },
    setDone: function() {
      this.styles.done = true;
    }
  },
  computed: {
    full: function() {
      return this.name + ' ' + this.surn;
    }
  }
}
</script>

<style scoped>
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

p.done {
  text-decoration: line-through;
}
</style>
