<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
    <button @click="updateTitle('New Title')">Change Title</button>
    <h1>{{ title }}</h1>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld,
  },
})
export default class HomeView extends Vue {
  @Prop({ default: () => [] }) todo!: Array<{
    id: number;
    text: string;
    done: boolean;
  }>;

  title = "Initial Title";

  @Emit("custom-event")
  updateTitle(newTitle: string) {
    this.title = newTitle;
    return newTitle;
  }
}
</script>
