<template>
  <nuxt-link :to="'/mochila#' + bucket.name | lowercase" class="tile" >

    <img
      class="tile__img"
      :src="bucket.thumbnail"
      :alt="bucket.name"/>

    <div class="tile__details">
      <div class="tile__title">
        <h2>{{ bucket.name | capitalize }}</h2>
        {{ bucket.description }}
      </div>
    </div>

  </nuxt-link>
</template>

<script>
export default{
  name: 'Bucket',
  props: {
    bucket: {
      type: Object,
      required: true,
    },
  }
}
</script>

<style lang="scss" scoped>

$transition: .45s;
$width: 250px;
$height: 499.094px;

.tile__details {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  top: 0;
  opacity: 0;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.9) 0%, rgba(0, 0, 0, 0) 100%);
  transition: $transition opacity;
}

.tile__title {
  position: absolute;
  bottom: 0;
  padding: 0 10px 2.5em 10px;
}

.tile__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.tile {
  float: left;
  position: relative;
  width: $width;
  height: $height;
	transition: transform $transition;
  text-decoration: none;
  color: white;
  margin: 0 3px;
}

.buckets:hover {
	.tile {
		transform: translateX(-10%);
	}

	.tile:hover {
		transform: scale(1.2);
		transition-duration: $transition/1.1;

    .tile__details {
      opacity: 1;
    }
	}

	.tile:hover ~ .tile {
		transform: translateX(10%);
	}
}

</style>
