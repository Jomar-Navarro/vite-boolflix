<script>
import card from "../components/part/card.vue";
import { store } from "../data/store";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper/modules";
export default {
	props: {
		type: String,
	},

	components: {
		card,
		Swiper,
		SwiperSlide,
	},

	data() {
		return {
			store,
			modules: [Pagination],
		};
	},
};
</script>

<template>
	<h1 class="text-white d-flex justify-content-center mt-5">
		<img src="/img/popular.png" alt="popular.png" />
	</h1>
	<div class="row row-cols-2 justify-content-center">
		<swiper
			:slidesPerView="5"
			:spaceBetween="0"
			:pagination="{
				clickable: true,
			}"
			:modules="modules"
			class="mySwiper w-100"
		>
			<swiper-slide v-for="item in store.popularList" :key="item.id">
				<div class="overflow-hidden">
					<div class="container text-center my-5">
						<card class="zoom" :cardObj="item" />
					</div>
				</div>
			</swiper-slide>
		</swiper>
	</div>
</template>

<style lang="scss" scoped>
.zoom:hover {
	-ms-transform: scale(1.1);
	-webkit-transform: scale(1.1);
	transform: scale(1.1);
}

.zoom {
	transition: transform 0.2s;
	margin: 0 auto;
}
</style>
