<template>
    <header class="AppHeader" :style="headerStyle">
        <div class="AppHeader__logo">
        	<router-link class="AppHeader__link" to="/">
				<div v-if="content.logo">
					<img class="AppHeader__img" :src="content.logo" :alt="content.title" />
				</div>
				<div v-else>
					<h1 class="AppHeader__title" :style="titleStyle">
						{{content.title}}
					</h1>	
				</div>
        	</router-link>
        </div>
		<div class="AppHeader__right">
			<el-button type="primary" :style="bookBtnStyle">
				Book Now
			</el-button>
		</div>   
    </header>
</template>

<style lang="scss">
.AppHeader {
	display: flex;
	padding: 0 20px;
	height: 60px;
	width: 100%;
	align-items: center;
	justify-content: space-between;

	&__logo {
		float: left;
	}

	&__link {
		text-decoration: none;
		font-size: 16px;
	}

	&__img {
		vertical-align: middle;
		width: 2.5rem;
		margin-right: 0.5rem;
	}

	&__title {
		font-weight: 400;
		text-transform: uppercase;
	}

	&__right {
		float: right;
	}
}
</style>

/**
 * Header 
 */
<script>
export default {
	name: "CvAppHeader",
	computed: {
		headerStyle () {
			const { primaryColor, tertiaryColor } = this.theme
			return {
				backgroundColor: tertiaryColor,
				borderBottomColor: primaryColor
			}
		},
		titleStyle () {
			const { primaryColor } = this.theme
			return {
				color: primaryColor
			}
		},
		bookBtnStyle () {
			const { primaryColor } = this.theme
			return {
				backgroundColor: primaryColor,
				borderColor: primaryColor
			}
		},
		content () {
			const { logo, companyName } = this.global
			return {
				logo,
				title: companyName
			}
		}
	},
	props: {
		global: {
			type: Object
		},
		theme: {
			type: Object
		}
	}
}
</script>
