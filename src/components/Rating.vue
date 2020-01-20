<template>
  <div class="rating">
    <h3>Rate this app</h3>
    <ul class="list">
      <li v-for="star in maxStars" :class="{ 'active': star <= stars }" :key="star"
          class="star" @click="rate(star)">
        <Icon :name="'star'"/>
      </li>
    </ul>
    <span v-if="hasCounter">{{ stars }} of {{ maxStars }}</span>
  </div>
</template>

<script>
import 'vue-awesome/icons/star';
import Icon from 'vue-awesome/components/Icon.vue';

export default {
  components: { Icon },
  props: {
    maxStars: Number,
    grade: Number,
    hasCounter: Boolean,
  },
  data() {
    return {
      stars: this.grade,
    };
  },
  methods: {
    rate(star) {
      if (star <= this.maxStars && star >= 0) {
        this.stars = this.stars === star ? star - 1 : star;
      }
    },
  },
};
</script>

<style scoped lang="scss">
  $active-color: #f3d23e;
  h3 {
    margin: 40px 0 0;
  }
  .rating {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 22px;
    color: #a7a8a8;
  }
  .list {
    margin: 0 0 5px 0;
    padding: 0;
    list-style-type: none;
    &:hover {
      .star {
        color: $active-color;
      }
    }
  }
  .star {
    display: inline-block;
    cursor: pointer;
    &:hover {
      &~.star {
        &:not(.active) {
          color: inherit;
        }
      }
    }
  }
  .active {
    color: $active-color;
  }
</style>
