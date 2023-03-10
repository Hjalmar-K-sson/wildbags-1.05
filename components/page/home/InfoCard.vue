<template>
  <div class="info-card" :class="{ 'info-card--ltr': direction === 'ltr', 'info-card--rtl': direction === 'rtl' }">
    <div class="info-card__section">
      <img class="info-card__img" :src="imgUrl" :alt="imgAlt" />
    </div>
    <div class="info-card__section">
      <h2 class="info-card__title">{{ title }}</h2>
      <div class="info-card__text-container">
        <p v-for="(item, id) in text" :key="id" class="info-card__text">{{ item }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  direction: 'ltr' | 'rtl';
  imgUrl: string;
  imgAlt: string;
  title: string;
  text: string[];
}>();
</script>

<style lang="scss" scoped>
.info-card {
  margin: 0 auto;
  width: 100%;
  padding: 2.4rem;

  @include tablet {
    padding: 4.8rem;
  }

  @include desktop-lg {
    padding: 6.4rem;
  }

  @include desktop-2xl {
    max-width: 80%;
    padding: 11.2rem;
  }

  &--ltr {
    @include flex(column);

    @include tablet-landscape {
      @include flex(row);
    }
  }

  &--rtl {
    @include flex(column-reverse);

    @include tablet-landscape {
      @include flex(row-reverse, null, flex-start);
      .info-card__section {
        gap: 4.8rem;
      }

      .info-card__text-container {
        gap: 3.2rem;
      }
    }
  }

  &__section {
    @include flex(column, flex-start, flex-start, 1.6rem);

    @include tablet-landscape {
      width: 50%;
    }
  }

  &__img {
    width: 100%;
    border-radius: 1rem;
  }

  &__title {
    font-size: 4.8rem;

    @include desktop {
      font-size: 5.6rem;
    }
  }

  &__text-container {
    @include flex(column, null, null, 1.6rem);
  }

  &__text {
    font-size: 1.8rem;
    letter-spacing: 0.15rem;

    @include tablet {
      font-size: 2.2rem;
    }

    @include tablet-landscape {
      font-size: 1.8rem;
    }

    @include desktop {
      font-size: 2.4rem;
    }
  }
}
</style>
