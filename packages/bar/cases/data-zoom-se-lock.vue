<template>
  <lc-bar
    style="width: 300px; height: 300px"
    :source="source"
    :dataZoom="{
      start: 20,
      end: 40,
      zoomLock: true,
    }"
  />
</template>
<script>
export default {
  data() {
    return {
      source: [
        ['', '水费', '电费'],
        ['1月', 43.3, 13.1],
        ['2月', 83.1, 2],
        ['4月', 86.4, 93.3],
        ['5月', 93.3, 60],
      ],
    }
  },
}
</script>
