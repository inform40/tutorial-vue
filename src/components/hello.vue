<template>
    <div>
        <div class="greeting">Hello {{name}}{{exclamationMarks}}</div>
        <button @click="decrement">-</button>
        <button @click="increment">+</button>
    </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class HelloDecorator extends Vue {
  @Prop() name!: string;
  @Prop() initialEnthusiasm!: number;

  enthusiasm = this.initialEnthusiasm;

  private increment() {
    this.enthusiasm++;
  }
  private decrement() {
    if (this.enthusiasm > 1) {
      this.enthusiasm--;
    }
  }

  private get exclamationMarks(): string {
    return Array(this.enthusiasm + 1).join("!");
  }
}
</script>

<style>
    .greeting {
        color: red;
    }
</style>

<documentation>
    Die Hallo Komponente sagt Hallo :)
</documentation>