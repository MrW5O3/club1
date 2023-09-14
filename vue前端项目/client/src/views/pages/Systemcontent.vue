<template>
	<div>
		<!-- 规则介绍 -->
		<h2 class="activeity-h2">学生社团管理条例</h2>
		<div class="activeity-time">时间：2023-09-05</div>
		<p class="activeity-nr">第1条 按照教育部和学校的要求，为了进一步规范四川大学学生社团（以下简称学生社团）的管理，
		推动学生社团健康、有序地发展，繁荣校园文化，促进校园精神文明建设，推进学生素质教育，
		依据《宪法》、《教育法》、《高等教育法》以及其他有关法律、法规，及校内有关规定制定本条例。
		</p>
	</div>
</template>

<script>
</script>

<style>
	.head-top {
	    width: 100%;
	    min-width: 1280px;
	    height: 40px;
	    background-color: #fa730d;
	    color: #fff;
	    line-height: 40px;
	}
	
	.head-top .wrap span {
	    display: inline-block;
	}
	
	.head-top .wrap .hy {
	    display: block;
	    float: right;
	}

	.head-top .wrap .hy .wx_2 {
		width: 200px;
		height: 200px;
		border-radius: 10px;
		position: absolute;
		top: -9999px;
		z-index: 5;
	}

	.head-top .wrap .hy .wx:hover~.wx_2 {
		position: absolute;
		top: 30px;
		right: 140px;
	}

	.head-top .wrap .hy .qq_2 {
		width: 200px;
		height: 200px;
		border-radius: 10px;
		position: absolute;
		top: -9999px;
		z-index: 5;
	}

	.head-top .wrap .hy .qq:hover~.qq_2 {
		position: absolute;
		top: 30px;
		right: 85px;
	}
	
	.head-top a {
	    color: #fff;
	    text-decoration:none;
	}
	
	.head-top a:hover{
	    color: red;
	}
	
	.head-top .dl {
	    width: 150px;
	    display: inline-block;
	    position: relative;
	    left: 795px;
	}
	
	.head-top .dl .gr {
	    width: 150px;
	    display: inline-block;
	    margin-top: 1px;
	    text-align: center;
	}

	.landscape {
		width: 1200px;
		height: 600px;
		position: relative;
		top: 40px;
		margin: 0 auto;
	}

	.landscape p {
		margin-top: 276px;
		font-size: 18px;
		color: rgb(255,255,255); 
		position: relative;
		top: -8px;
		left: 5px;
	}

	.landscape .first_line {
		width: 1200px;
		height: 295px;
		margin: 0 auto;
	}

	.landscape .second_line {
		width: 1200px;
		height: 295px;
		margin: 0 auto;
		position: relative;
		top: 10px;
	}

	.landscape .first_line .tp_1 {
		width: 330px;
		height: 295px;
		background-image: url(../../assets/校园风光01.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
		margin-right: 10px;
	}

	.landscape .first_line .tp_2 {
		width: 330px;
		height: 295px;
		background-image: url(../../assets/校园风光02.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
		margin-right: 10px;
	}

	.landscape .first_line .tp_3 {
		width: 520px;
		height: 295px;
		background-image: url(../../assets/校园风光04.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
	}

	.landscape .first_line div:hover {
		box-shadow: 0 3px 3px 0 grey;
		transform: translate(0, -5px);
		transform: scale(1.1)
	}

	.landscape .second_line .tp_4 {
		width: 330px;
		height: 295px;
		background-image: url(../../assets/校园风光03.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
	}

	.landscape .second_line .tp_5 {
		width: 330px;
		height: 295px;
		background-image: url(../../assets/校园风光05.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
		margin-right: 10px;
	}

	.landscape .second_line .tp_6 {
		width: 520px;
		height: 295px;
		background-image: url(../../assets/校园风光06.jpg);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: cover;
		display: inline-block;
		margin-right: 10px;
	}

	.landscape .second_line div:hover {
		box-shadow: 0 3px 3px 0 grey;
		transform: translate(0, -5px);
		transform: scale(1.1)
	}
</style>