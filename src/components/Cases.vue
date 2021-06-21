<template>
	<div class="row my-3">
		<div class="col-lg-4 col-md-6 py-3">
			<div class="card shadow pb-3">
				<div class="card-body">
					<h1 class="display-3"> {{ Comma(stats.recovered) }} </h1>
					<h2 class="h2 fw-bold text-success"> <i class="fas fa-head-side-mask"></i> R E C O V E R  </h2>
				</div>
			</div>
		</div>
		<div class="col-lg-4 col-md-6 py-3">
			<div class="card shadow pb-3">
				<div class="card-body">
					<h1 class="display-3"> {{ Comma(stats.confirmed) }} </h1>
					<h2 class="h2 fw-bold text-warning"> <i class="fas fa-head-side-virus"></i> Cofirmed</h2>
				</div>
			</div>
		</div>
		<div class="col-lg-4 py-3">
			<div class="card shadow pb-3">
				<div class="card-body">
					<h1 class="display-3 "> {{ Comma(stats.dead) }} </h1>
					<h2 class="h2 fw-bold text-danger"> <i class="fas fa-head-side-cough"></i> Dead</h2>
				</div>
			</div>
		</div>
	</div>
</template>
<style></style>
<script>
	export default {
  name: 'Cases',
  props: ['stats'], 
  methods:{
  	 Comma (x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
      }
  }
}
</script>