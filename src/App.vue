<template>
  <div>
    <h2>Flex playground</h2>

    <div>
      <h3>justify-content</h3>
      <div>
        <button @click="setJustifyContent('flex-start')">start</button>
        <button @click="setJustifyContent('center')">center</button>
        <button @click="setJustifyContent('space-between')">space-between</button>
        <button @click="setJustifyContent('space-around')">space-around</button>
      </div>
    </div>
    <div>
      <h3>Align-Items</h3>
      <div>
        <button @click="setAlignItems('stretch')">stretch</button>
        <button @click="setAlignItems('center')">center</button>
        <button @click="setAlignItems('start')">start</button>
        <button @click="setAlignItems('end')">end</button>
      </div>
    </div>

    <h3>Code</h3>
    <button @click="toggleCodeVisibility">
      {{ codeVisible ? 'Hide code' : 'Show code' }}
    </button>
    <div v-if="codeVisible">
      <pre>
        <code>{{ code }}</code>
      </pre>
    </div>

    <div class="flex-box" :style="{ justifyContent: justifyContent, alignItems: alignItems }">
      <div class="flex-item">One</div>
      <div class="flex-item">Two</div>
      <div class="flex-item">Tree</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      code: '',
      codeVisible: false,
      justifyContent: 'flex-start',
      alignItems: 'start',
    };
  },
  mounted() {
    this.updateCode()
  },
  methods: {
    setJustifyContent(value) {
      this.justifyContent = value;
      this.updateCode();
    },
    setAlignItems(value) {
      this.alignItems = value;
      this.updateCode();
    },
    toggleCodeVisibility() {
      this.codeVisible = !this.codeVisible;
    },
    updateCode() {
      this.code = `
.flex-box {
  display: flex;
  justify-content: ${this.justifyContent};
  align-items: ${this.alignItems};
}
      `;
    },
  },
};
</script>

<style>
.flex-box {
  display: flex;
  width: 600px;
  height: 300px;
  border: 1px solid #000000;
  align-items: start;
}

.flex-item {
  width: 100px;
  height: 50px;
  background-color: aqua;
}
</style>
