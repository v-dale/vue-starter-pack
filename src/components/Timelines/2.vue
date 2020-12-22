<template>


	<div class="container">
    <h1 class="project-name">{{title}}</h1>
		<div id="timeline">
			<div v-for="subject in subjects" :key="subject.id" class="timeline-item">
				<div class="timeline-icon">
					<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                        width="21px" height="20px" viewBox="0 0 21 20" enable-background="new 0 0 21 20" xml:space="preserve">
                    <path fill="#FFFFFF" d="M19.998,6.766l-5.759-0.544c-0.362-0.032-0.676-0.264-0.822-0.61l-2.064-4.999
                        c-0.329-0.825-1.5-0.825-1.83,0L7.476,5.611c-0.132,0.346-0.462,0.578-0.824,0.61L0.894,6.766C0.035,6.848-0.312,7.921,0.333,8.499
                        l4.338,3.811c0.279,0.246,0.395,0.609,0.314,0.975l-1.304,5.345c-0.199,0.842,0.708,1.534,1.468,1.089l4.801-2.822
                        c0.313-0.181,0.695-0.181,1.006,0l4.803,2.822c0.759,0.445,1.666-0.23,1.468-1.089l-1.288-5.345
                        c-0.081-0.365,0.035-0.729,0.313-0.975l4.34-3.811C21.219,7.921,20.855,6.848,19.998,6.766z"/>
                    </svg>

				</div>
				<div class="timeline-content" :class="{'right': subject.id % 2 == 0}">
					<h2>{{subject.name}}</h2>
					<p>{{subject.description}}</p>

				</div>
			</div>

	
		</div>
	</div>


        
</template>

<script>
export default {
    props: {
        title:String,
        subjects: Array
    },

}
</script>

<style lang="scss" scoped>

@import "https://fonts.googleapis.com/css?family=Dosis:300,400,500,600,700";
// Variables
$bg-body: #f9f9f9;

$red: #ee4d4d;
$blue: #2b2e48;
$primary-color: $red;
$secondary-color: $blue;


// Typography
$base-font: helvetica, arial, tahoma, verdana;
$base-font-title: "Dosis", arial, tahoma, verdana;

$base-font-color: #726f77;

// Timeline
$timeline-color: $primary-color;


// Mixins and Placeholders
%clearfix {
	&:after, &:before {
		content: '';
		display: block;
		width: 100%;
		clear: both;
	}
}

@mixin prefix($prop, $val) {
	@each $prefix in '-webkit-', '-moz-', '-ms-', '' {
		#{$prefix}#{$prop}: $val;
	}
}
*, *:before, *:after {
	box-sizing: border-box;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
}



img {max-width: 100%;}


.container {
	max-width: 1100px;
	margin: 0 auto;
}



// Timeline
#timeline {
	width: 100%;
    margin: 30px auto;
	position: relative;
    padding: 0 10px;
	@include prefix(transition, all .4s ease);

	&:before {
		content:"";
		width: 3px;
		height: 100%;
		background: $timeline-color;
		left: 50%;
		top: 0;
		position: absolute;
	}

	&:after {
		content: "";
		clear: both;
		display: table;
		width: 100%;
	}
	
	.timeline-item {
		margin-bottom: 50px;
		position: relative;
		@extend %clearfix;

		.timeline-icon {
			background: $timeline-color;
			width: 50px;
			height: 50px;
			position: absolute;
			top: 0;
			left: 50%;
			overflow: hidden;
			margin-left: -25px;
			@include prefix(border-radius, 50%);

			svg {
				position: relative;
				top: 14px;
				left: 2px;
			}
		}

		.timeline-content {
			width: 45%;
			background: #fff;
			padding: 20px;
			@include prefix(box-shadow, 0 3px 0 rgba(0,0,0,0.1));
			@include prefix(border-radius, 5px);
			@include prefix(transition, all .3s ease);

			h2 {
				padding: 15px;
				background: $timeline-color;
				color: #fff;
				margin: -20px -20px 0 -20px;
				font-weight: 300;
				@include prefix(border-radius, 3px 3px 0 0);
			}

			&:before {
				content: '';
				position: absolute;
				left: 45%;
				top: 20px;
				width: 0; 
				height: 0; 
				border-top: 7px solid transparent;
				border-bottom: 7px solid transparent; 
				border-left:7px solid $timeline-color; 
			}

			&.right {
				float: right;

				&:before {
					content: '';
					right: 45%;
					left: inherit;
					border-left: 0;
					border-right: 7px solid $timeline-color;
				}
			}
		}
	}
}



@media screen and (max-width: 768px) {
	#timeline {
		margin: 30px;
		padding: 0px;
        width: 90%;
		&:before {
			left: 0;
		}
		
		.timeline-item {
			.timeline-content {
				width: 90%;
				float: right;
				
				&:before, &.right:before {
					left: 10%;
					margin-left: -6px;
					border-left: 0;
					border-right: 7px solid $timeline-color;
				}
			}

			.timeline-icon {
				left: 0;
			}
		}
	}
}

</style>