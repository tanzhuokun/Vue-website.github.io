<template>
  <div id="switch" class="switch" @click.stop="toggle()" :style="{backgroundColor:this.options.contentbg}">
  	<span class="range" ref="switch_range" :style="rangeStyleInfo"></span>
  </div>
</template>
<script>
var oSwitch = document.getElementById('switch')
// var App = document.getElementById('app')
var flag = false
oSwitch.onclick = function () {
	if (!flag) {
		document.body.style.backgroundImage = "url('http://www.fanjiani.club/wp-content/uploads/2019/09/205221z0shtuju5bjqk1vf.jpg')!important"
        this.flag = !this.flag
	} else {
		this.flag = !this.flag
	}
}
</script>
<script>
  export default {
  	data () {
  		return {
  			// isactive: this.isActive,
  			// styleinfo: {
  			// 	rangebg: this.rangeBg,
  			// 	rangeactivebg: this.rangeActiveBg,
  			// 	contentbg: this.contentBg
  			// }
  		}
  	},
  	props: {
  		// isActive: {
  		// 	type: Boolean
  		// },
  		// rangeBg: {
  		// 	type: String
  		// },
  		// contentBg: {
  		// 	type: String
  		// },
  		// rangeActiveBg: {
  		// 	type: String
  		// }
  		options: {
  		}
  	},
  	methods: {
  		toggle () {
  			const ref = this.options.ref
  			this.options.isactive = !this.options.isactive
  			const callback = {
  				ref: ref,
  				active: this.options.isactive
  			}
  			this.$emit('selectBgType', callback)
  		}
  	},
  	computed: {
  		rangeStyleInfo () {
  			let styleInfo = {}
  			if (this.options.isactive) {
  				styleInfo.backgroundColor = this.options.rangeactivebg
  				styleInfo.transform = `translate(100%,0)`
  			} else {
  				styleInfo.backgroundColor = this.options.rangebg
  				styleInfo.transform = `translate(0,0)`
				}
				console.log(this.options)
  			return styleInfo
  		}
  	}
  }
</script>
<style lang="stylus" rel="stylesheet/stylus">
@import '~common/stylus/global.styl'
	.switch
		width:38px;
		height:20px;
		border-radius:10px
		cursor:pointer
		.range
			width:18px
			height:18px
			border-radius:50%
			background:#fff
			display: inline-block
			margin-left: 1px
			margin-top: 1px
			vertical-align: top
			transition:0.5s ease
</style>
