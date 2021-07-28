<template>
  <div :style="containerStyle">

    <iframe :id="id" :name="name" :allow="allow" :height="iframeHeight" :width="iframeWidth" :allowfullscreen="allowfullscreen" :mozallowfullscreen="allowfullscreen" :msallowfullscreen="allowfullscreen" :webkitallowfullscreen="allowfullscreen" :frameborder="frameborder" :src="src" :allowtransparency="allowtransparency" :referrerpolicy="referrerpolicy" ></iframe>

  </div>  
</template>

<script>

module.exports = {
  name: 'IFrame',
  props: { 
    items: { type: Array, default: () => ([]) },
    viewerIsActive: Boolean
  },
  data: () => ({
    viewerLabel: 'IFrame',
    viewerIcon: 'fas fa-history',
    dependencies: [],
    height: 750,
  }),
  computed: {
    containerStyle() { return { 
      position: 'relative',
      height: this.viewerIsActive ? '100%' : '0', 
      overflowY: 'auto !important' 
    }},
    filteredItems() { return this.items.filter(item => item[this.componentName]) },
    item() { return this.filteredItems[0] },
    id() { return this.item.id || '' },
    name() { return this.item.name || '' },
    allow() { return this.item.allow || '' },
    iframeHeight() { return this.item.height || '' },
    iframeWidth() { return this.item.width || '' },
    allowfullscreen() { return this.item.allowfullscreen || 'true' },
    src() { return this.item.src || '' },
    srcdoc() { return this.item.srcdoc || '' },
    allowtransparency() { return this.item.allowtransparency || 'true' },
    referrerpolicy() { return this.item.referrerpolicy || '' },
    sandbox() { return this.item.sandbox || '' },
    frameborder() { return this.item.frameborder || '0' }
  },
  mounted() { this.loadDependencies(this.dependencies, 0, this.init) },
  methods: {
    init() {
    }
  }
}
</script>

<style>
</style>