<template>
  <div :class="starType" class="star">
    <span class="star-item"
          :class="itemClass"
          v-for="itemClass in itemClasses"
          :key="itemClass.id">
    </span>
  </div>
</template>
<script type="text/ecmascript-6">
  const LENGTH = 5
  const CLS_ON = 'on'
  const CLS_HALF = 'half'
  const CLS_OFF = 'off'
  export default {
    props: {
      size: {
        type: Number
      },
      score: {
        type: Number
      }
    },
    computed: {
      starType() {
        return `star-${this.size}`
      },
      itemClasses() {
        let result = []
        let score = Math.floor(this.score * 2) / 2
        let hasDecimal = score % 1 !== 0
        let integer = Math.floor(score)
        for (let i = 0; i < integer; i++) {
          result.push(CLS_ON)
        }
        if (hasDecimal) {
          result.push(CLS_HALF)
        }
        while (result.length < LENGTH) {
          result.push(CLS_OFF)
        }
        return result
      }
    }
  }
</script>
<style scoped lang="scss">
  .star {
    font-size: 0;
    .star-item {
      display: inline-block;
      background-repeat: no-repeat;
    }
    &.star-48 {
      .star-item {
        width: 20px;
        height: 20px;
        background-size: cover;
        margin-right: 22px;
        &:last-child {
          margin-right: 0;
        }
        &.on {
          @include bg-img('star48_on');
        }
        &.half {
          @include bg-img('star48_half');
        }
        &.off {
          @include bg-img('star48_off');
        }
      }
    }
    &.star-36 {
      .star-item {
        width: 15px;
        height: 15px;
        background-size: cover;
        margin-right: 6px;
        &:last-child {
          margin-right: 0;
        }
        &.on {
          @include bg-img('star36_on');
        }
        &.half {
          @include bg-img('star36_half');
        }
        &.off {
          @include bg-img('star36_off');
        }
      }
    }
    &.star-24 {
      .star-item {
        width: 10px;
        height: 10px;
        background-size: cover;
        margin-right: 3px;
        &:last-child {
          margin-right: 0;
        }
        &.on {
          @include bg-img('star24_on');
        }
        &.half {
          @include bg-img('star24_half');
        }
        &.off {
          @include bg-img('star24_off');
        }
      }
    }
  }
</style>
