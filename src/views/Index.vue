<template>
	<div>	
	<div class="xu-row">
		<div class="xu-col-8">
			<div class="xu-row">
				<div class="xu-col-3" v-for="(article, index) in articles" :key="index">
					<li onClick="location.href='Nav.vue';">
						<img :src="article.cover" referrerpolicy ="never" width="200" height="300" />
						<div class="post-info">
							<div class="post-basic-info">
								<h3>
									<a>{{ article.title }}</a>
								</h3>
								<span>
									<div class="active">
										<label>{{article.content}}</label>
										
									</div>
									<div class="time">
										<p>{{article.nickname}}</p>
										
									</div>
								</span>
								<p></p>
							</div>
							<div class="post-info-rate-share">
								<div class="rateit"><span></span></div>
								<div class="post-share"><span></span></div>
								<div class="clear"></div>
							</div>
						</div>
					</li>
				</div>
			</div>
		</div>
		<div class="xu-col-4"></div>
	</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			articles: []
		};
	},
	created() {
		this.axios.get('http://localhost:8080/article').then(res => {
			console.log(res.data.data);
			this.articles = res.data.data;
		    for (var i = 0; i < this.articals.length; i++) {
		    				this.articals[i].avatar = this.getImage(this.articals[i].avatar);
		    			}
		});
	},
	methods: {
		getImage(url) {
					return 'https://images.weserv.nl/?url=' + url;
	}
	},
	computed: {
		
	}
	
};
</script>

<style scoped>
	li{
		list-style: none;
	}
	.xu-col-3{
		margin-left: 50px;
		margin-top: 100px;
	}
</style>
