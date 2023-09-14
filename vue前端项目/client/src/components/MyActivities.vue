<template>
	<!-- 我的活动 -->
	    <div class="myactivities">
	        <ul class="myactivities-tabulation">
	            <li><a href="#">我的活动</a></li>
	        </ul>
	        <div class="myactivities-bulk">
	            <div class="myactivities-bulk-top">
	                <h3>我的活动</h3>
	            </div>
	            <el-table v-if="pageInfos.length" v-loading="loading" element-loading-text="拼命加载中" element-loading-spinner="el-icon-loading"
	            	element-loading-background="rgba(124, 124, 124, 0.8)" :data="pageInfos" border>
	            	<el-table-column align="center" type="index"></el-table-column>
	            	<el-table-column align="center" prop="title" label="通知标题"></el-table-column>
	            	<el-table-column align="center" prop="teamId" label="发布社团"></el-table-column>
	            	<el-table-column align="center" prop="createTime" label="发布时间"></el-table-column>
	            	<el-table-column align="center" prop="detail" label="通知详情"></el-table-column>
	            </el-table>
				<el-table v-if="sysNotices.length" v-loading="loading" element-loading-text="拼命加载中" element-loading-spinner="el-icon-loading"
					element-loading-background="rgba(124, 124, 124, 0.8)" :data="sysNotices" border>
					<el-table-column align="center" type="index"></el-table-column>
					<el-table-column align="center" prop="title" label="通知标题"></el-table-column>
					<el-table-column align="center" prop="id" label="通知类型"></el-table-column>
					<el-table-column align="center" prop="createTime" label="发布时间"></el-table-column>
					<el-table-column align="center" prop="detail" label="通知详情"></el-table-column>
				</el-table>
	        </div>
	    </div>
</template>

<script>
	import {
		getManTeamList,
		getLoginUser,
		getPageNotices,
		getSysNoticeList
	} from "../api";
	
	export default {
	
		data() {
	
			return {
				sysNotices: [],
				teams: [],
				userType: "",
				pageInfos: [],
				pageIndex: 1,
				pageSize: 10,
				pageTotal: 0,
				totalInfo: 0,
				loading: true,
				showAddFlag: false,
				qryForm: {
					token: this.$store.state.token,
					teamName: "",
					title: "",
				},
				noticesForm: {
					id: "",
					title: "",
					detail: "",
					teamId: null,
				}
			}
		},
		methods: {
	
			getPageInfo(pageIndex, pageSize) {
	
				getPageNotices(pageIndex, pageSize, this.qryForm.token).then(resp => {
	
					this.pageInfos = resp.data.data;
					this.pageIndex = resp.data.pageIndex;
					this.pageSize = resp.data.pageSize;
					this.pageTotal = resp.data.pageTotal;
					this.totalInfo = resp.data.count;
	
					this.loading = false;
				});
			}
		},
		mounted() {
	
			this.getPageInfo(1, this.pageSize, this.qryForm.token);
	
			getLoginUser(this.$store.state.token).then(resp =>{
	
				this.userType = resp.data.type;
	
				getManTeamList(resp.data.id).then(resp =>{
	
					this.teams = resp.data;
				});
			});
			getSysNoticeList(this.$store.state.token).then(resp =>{
			
			    this.sysNotices = resp.data;
				for(let i = 0; i < this.sysNotices.length; i++){
					this.sysNotices[i].id = "系统通知";
				}
			});
		}
	}
</script>

<style>
	.myactivities {
	    width: 1200px;
	    height: 700px;
	    margin: 0 auto;
	}
	
	.myactivities .myactivities-tabulation {
	    width: 220px;
	    height: 75px;
	    display: inline-block;
	    list-style: none;
	    text-align: center;
	    line-height: 50px;
	    border: 1px solid #e9e9ee;
	    position: relative;
	}
	
	.myactivities .myactivities-tabulation li {
	    width: 180px;
	    margin: 0 auto;
	    border-bottom: 2px solid #e9e9ee;
	}
	
	.myactivities .myactivities-tabulation li a {
	    font-size: 25px;
	    font-family: 仿宋;
	    color: #fa730d;
	    text-decoration: none;
	}
	
	.myactivities .myactivities-bulk {
	    width: 940px;
	    height: 700px;
	    position: relative;
	    top: -75px;
	    left: 300px;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-top {
	    width: 940px;
	    height: 49px;
	    background-color: #fff;
	    line-height: 50px;
	    border-bottom: 1px solid #a1a1a1;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-top h3 {
	    width: 100px;
	    height: 50px;
	    color: #616161;
	    text-align: center;
	    border-bottom: 3px solid #fa730d;
	}
	
	.myactivities .myactivities-bulk ul {
	    width: 940px;
	    height: 550px;
	    background-color: #fff;
	    position: relative;
	    top: 40px;
	}
	
	.myactivities .myactivities-bulk ul li {
	    width: 940px;
	    height: 70px;
	    list-style: none;
	    padding-left: 5px;
	    padding-top: 12px;
	}
	
	.myactivities .myactivities-bulk ul li .time {
	    display: inline-block;
	    position: relative;
	    top: -10px;
	}
	
	.myactivities .myactivities-bulk ul li .state {
	    display: inline-block;
	    font-size: 32px;
	    color: #fa730d;
	    position: relative;
	    top: -20px;
	    left: 560px;
	}
	
	.myactivities .myactivities-bulk ul li h4 {
	    width: 500px;
	}
	
	.myactivities .myactivities-bulk ul li:nth-child(2n-1){
	    background-color: #eaeaeafb;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-bottom {
	    width: 940px;
	    height: 36px;
	    font-size: 12px;
	    color: #222;
	    position: relative;
	    top: 65px;
	    line-height: 36px;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-bottom .up {
	    width: 30px;
	    height: 20px;
	    border: 1px solid #ccc;
	    text-align: center;
	    line-height: 17px;
	    display: inline-block;
	    position: relative;
	    left: 390px;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-bottom .leaf {
	    width: 20px;
	    height: 20px;
	    background-color: #ff4848;
	    text-align: center;
	    line-height: 18px;
	    border: none;
	    display: inline-block;
	    position: relative;
	    left: 390px;
	}
	
	.myactivities .myactivities-bulk .myactivities-bulk-bottom .down {
	    width: 30px;
	    height: 20px;
	    border: 1px solid #ccc;
	    text-align: center;
	    line-height: 17px;
	    display: inline-block;
	    position: relative;
	    left: 390px;
	}
</style>