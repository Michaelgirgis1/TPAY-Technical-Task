<template>
  <div class="listing-loader">
    <img src="../assets/images/loader.gif" alt="listing loader" />
  </div>
</template>
<script>
// import { ar, en } from "vuejs-datepicker/dist/locale";

export default {
  name: "listingLoader"
};
</script>
<style lang="scss" scoped>
.listing-loader {
	display: flex;
	justify-content: center;
	align-items: center;
	margin-bottom: 50px;
	img {
		max-width: 68px;
		filter: brightness(var(--loader-filter));
	}
}
@media (max-width: 1366px) {
	.listing-loader {
		margin-bottom: 25px;
	}	
}
</style>