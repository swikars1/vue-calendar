<template>
  <div :class="[showTooltip ? 'tooltip' : 'header']">
    <slot />
    <div :class="{ hide: !showTooltip }">
      <div :class="{ hide: !$slots.title }">
        {{ title }}
      </div>
      <span class="tooltiptext">
          <div v-for="tooltip in tooltipList" :key="tooltip.title">
            {{ tooltip.title }}
          </div>
      </span>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    showTooltip: {
      type: Boolean,
      default: true,
    },
    title: {
      type: String,
      default: "",
    },
    tooltipList: {
      type: Array,
      default: () => [],
    }
  }
}
</script>
<style>
.tooltip {
  position: relative;
  display: inline-block;
  border-bottom: 1px dotted black;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 120px;
  background-color: black;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 5px 0;

  /* Position the tooltip */
  position: absolute;
  z-index: 1;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
}
.hide {
  display: none;
}
</style>
