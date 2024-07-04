<script setup>
import vModelBinding from './components/vModelBinding.vue';
import CheckBoxArray from './components/CheckBoxArray.vue';
import value from './data/data'
import { ref, reactive } from 'vue'
import { address, people } from './data/data'

const location = ref('Tangail')

function changeEvent(event) {
  location.value = event;
}
const image = ref('');

function imageEvent(event) {
  image.value = event.image;

}

const activeIndex = ref(0);

const details = reactive([
  {
    heading: "click now 1",
    content: "Like Anakin said, it’s woooorking! All of our icons are now ready to do your project’s bidding. Learn how to add them to your Vue project and then use their power to bring order and style to your UI!",
    isOpen: true
  }, {
    heading: "click now 2",
    content: "Like Anakin said, it’s woooorking! All of our icons are now ready to do your project’s bidding. Learn how to add them to your Vue project and then use their power to bring order and style to your UI!",
    isOpen: false
  },
  {
    heading: "click now 3",
    content: "Like Anakin said, it’s woooorking! All of our icons are now ready to do your project’s bidding. Learn how to add them to your Vue project and then use their power to bring order and style to your UI!",
    isOpen: true
  },
]);

// event modify
const spaceTitle = ref('Space Count Vue 3');
const space = ref(0);

function spacePressed() {
  space.value++;
  spaceTitle.value = "Total Space Pressed :" + space.value;
}
function PressedWhat(event) {
  space.value++;
  spaceTitle.value = " Space Pressed Count  :"+" " + space.value+ "and Space Key :"+event.key;
}

</script>

<template>

  <div class="  p-3" v-for="detail in details">
    <div @click="detail.isOpen = !detail.isOpen"
      class="bg-slate-700 text-white space-y-0.5 scroll-pb-0.5 cursor-pointer transition  hover:bg-current-500 flex space-x-4 px-5 h-15 items-center">
      <h1>{{ detail.heading }}</h1>
    </div>
    <div class="px-5 pt-0 text-left" v-show="detail.isOpen">
      <p>{{ detail.content }}</p>

    </div>

  </div>

  <h2>one index open other index auto hidden processing</h2>
  <div class="  p-3" v-for="(detail, index) in details">
    <div @click="activeIndex = index"
      class="bg-slate-700 text-white space-y-0.5 scroll-pb-0.5 cursor-pointer transition  hover:bg-current-500 flex space-x-4 px-5 h-15 items-center">
      <h1>{{ detail.heading }}</h1>
    </div>
    <div class="px-5 pt-0 text-left" v-show="activeIndex == index">
      <p>{{ detail.content }}</p>

    </div>

  </div>

  <button class="btn" type="button" @click="changeEvent('Dhaka')"> Dhaka</button>

  <button class="btn" type="button" @click="changeEvent('Tangail')"> Tangail</button>

  <h1 class="text-3xl font-bold underline">
    {{ location }}
  </h1>
  <h1>Name:{{ value.name }}</h1>
  <h1>date:{{ value.date }}</h1>
  <h1>Addres:{{ address }}</h1>
  <section class="bg-red-100">
    <h1 style="text-align:center;margin:40px 0px;font-size:40px">Data Example</h1>
    <section class="content ">
      <section class="person" v-for="(data, index) in people" :key="index">
        <img :src="data.image" @click="imageEvent(data)" alt="Jane Doe">
        <div>

          <h1>{{ data.name }}</h1>
          <h2>{{ data.designation }}</h2>
          <p>{{ data.location }}</p>
        </div>
      </section>
      <section style="padding: 10%;">
        <img :src="image" alt="Jane Doe">
      </section>
    </section>
  </section>

  <section class="p-5">
    <form class="max-w-sm mx-auto">
      <div class="mb-5">
        <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">{{ spaceTitle }}</label>
        <input type="text" @keyup.space="spacePressed()" id="email"
          class="bg-red-50 border border-red-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="enter value" required />
      </div>
      <div class="mb-5">
        <input type="text" @keyup="PressedWhat($event)" placeholder="Enter pressed key find" id="password"
          class="bg-gray-50 border border-red-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          required />
      </div>
      <button type="submit"
        class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
    </form>
  </section>

<vModelBinding/>
<CheckBoxArray/>
</template>

<style scoped>
.btn {
  padding: 5px;
  margin: 10px;
  background-color: aqua;
}

.content {
  width: 100%;
  margin-right: auto;
  margin-left: auto
}

@media (min-width:640px) {
  .content {
    max-width: 640px
  }
}

@media (min-width:768px) {
  .content {
    max-width: 768px
  }
}

@media (min-width:1024px) {
  .content {
    max-width: 1024px
  }
}

@media (min-width:1280px) {
  .content {
    max-width: 1280px
  }
}

@media (min-width:1536px) {
  .content {
    max-width: 1536px
  }
}

.content {
  display: grid;
  gap: 1.25rem;
  grid-template-columns: repeat(3, minmax(0, 1fr))
}

.person img {
  --tw-bg-opacity: 1;
  background-color: rgba(191, 219, 254, var(--tw-bg-opacity))
}

.person div {
  margin-top: 1.25rem
}

.person h1 {
  font-size: 1.5rem;
  line-height: 2rem
}

.person h2 {
  font-size: 1.25rem;
  line-height: 1.75rem;
  margin-top: .5rem
}

.person p {
  margin-top: .5rem;
  --tw-text-opacity: 1;
  color: rgba(107, 114, 128, var(--tw-text-opacity))
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale
}

/*! tailwindcss v2.1.2 | MIT License | https://tailwindcss.com */
/*! modern-normalize v1.0.0 | MIT License | https://github.com/sindresorhus/modern-normalize */
*,
::after,
::before {
  box-sizing: border-box
}

:root {
  -moz-tab-size: 4;
  -o-tab-size: 4;
  tab-size: 4
}

html {
  line-height: 1.15;
  -webkit-text-size-adjust: 100%
}

body {
  margin: 0
}

body {
  font-family: system-ui, -apple-system, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji'
}

hr {
  height: 0;
  color: inherit
}

abbr[title] {
  -webkit-text-decoration: underline dotted;
  text-decoration: underline dotted
}

b,
strong {
  font-weight: bolder
}

code,
kbd,
pre,
samp {
  font-family: ui-monospace, SFMono-Regular, Consolas, 'Liberation Mono', Menlo, monospace;
  font-size: 1em
}

small {
  font-size: 80%
}

sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline
}

sub {
  bottom: -.25em
}

sup {
  top: -.5em
}

table {
  text-indent: 0;
  border-color: inherit
}

button,
input,
optgroup,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
  line-height: 1.15;
  margin: 0
}

button,
select {
  text-transform: none
}

[type=button],
button {
  -webkit-appearance: button
}

legend {
  padding: 0
}

progress {
  vertical-align: baseline
}

summary {
  display: list-item
}

blockquote,
dd,
dl,
figure,
h1,
h2,
h3,
h4,
h5,
h6,
hr,
p,
pre {
  margin: 0
}

button {
  background-color: transparent;
  background-image: none
}

button:focus {
  outline: 1px dotted;
  outline: 5px auto -webkit-focus-ring-color
}

fieldset {
  margin: 0;
  padding: 0
}

ol,
ul {
  list-style: none;
  margin: 0;
  padding: 0
}

html {
  font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  line-height: 1.5
}

body {
  font-family: inherit;
  line-height: inherit
}

*,
::after,
::before {
  box-sizing: border-box;
  border-width: 0;
  border-style: solid;
  border-color: #e5e7eb
}

hr {
  border-top-width: 1px
}

img {
  border-style: solid
}

textarea {
  resize: vertical
}

input::-moz-placeholder,
textarea::-moz-placeholder {
  opacity: 1;
  color: #9ca3af
}

input:-ms-input-placeholder,
textarea:-ms-input-placeholder {
  opacity: 1;
  color: #9ca3af
}

input::placeholder,
textarea::placeholder {
  opacity: 1;
  color: #9ca3af
}

button {
  cursor: pointer
}

table {
  border-collapse: collapse
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: inherit
}

a {
  color: inherit;
  text-decoration: inherit
}

button,
input,
optgroup,
select,
textarea {
  padding: 0;
  line-height: inherit;
  color: inherit
}

code,
kbd,
pre,
samp {
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace
}

audio,
canvas,
embed,
iframe,
img,
object,
svg,
video {
  display: block;
  vertical-align: middle
}

img,
video {
  max-width: 100%;
  height: auto
}

.container {
  width: 100%;
  margin-right: auto;
  margin-left: auto
}

@media (min-width:640px) {
  .container {
    max-width: 640px
  }
}

@media (min-width:768px) {
  .container {
    max-width: 768px
  }
}

@media (min-width:1024px) {
  .container {
    max-width: 1024px
  }
}

@media (min-width:1280px) {
  .container {
    max-width: 1280px
  }
}

@media (min-width:1536px) {
  .container {
    max-width: 1536px
  }
}

.table {
  display: table
}

.grid {
  display: grid
}

.mt-2 {
  margin-top: .5rem
}

* {
  --tw-shadow: 0 0 #0000
}

* {
  --tw-ring-inset: var(--tw-empty, );
  /*!*/
  /*!*/
  --tw-ring-offset-width: 0px;
  --tw-ring-offset-color: #fff;
  --tw-ring-color: rgba(59, 130, 246, 0.5);
  --tw-ring-offset-shadow: 0 0 #0000;
  --tw-ring-shadow: 0 0 #0000
}

.grid-cols-3 {
  grid-template-columns: repeat(3, minmax(0, 1fr))
}

@-webkit-keyframes spin {
  to {
    transform: rotate(360deg)
  }
}

@keyframes spin {
  to {
    transform: rotate(360deg)
  }
}

@-webkit-keyframes ping {

  100%,
  75% {
    transform: scale(2);
    opacity: 0
  }
}

@keyframes ping {

  100%,
  75% {
    transform: scale(2);
    opacity: 0
  }
}

@-webkit-keyframes pulse {
  50% {
    opacity: .5
  }
}

@keyframes pulse {
  50% {
    opacity: .5
  }
}

@-webkit-keyframes bounce {

  0%,
  100% {
    transform: translateY(-25%);
    -webkit-animation-timing-function: cubic-bezier(.8, 0, 1, 1);
    animation-timing-function: cubic-bezier(.8, 0, 1, 1)
  }

  50% {
    transform: none;
    -webkit-animation-timing-function: cubic-bezier(0, 0, .2, 1);
    animation-timing-function: cubic-bezier(0, 0, .2, 1)
  }
}

@keyframes bounce {

  0%,
  100% {
    transform: translateY(-25%);
    -webkit-animation-timing-function: cubic-bezier(.8, 0, 1, 1);
    animation-timing-function: cubic-bezier(.8, 0, 1, 1)
  }

  50% {
    transform: none;
    -webkit-animation-timing-function: cubic-bezier(0, 0, .2, 1);
    animation-timing-function: cubic-bezier(0, 0, .2, 1)
  }
}
</style>
