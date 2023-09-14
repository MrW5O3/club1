<template>
	<div>
		<!-- 活动介绍 -->
		<h2 class="activeity-h2">{{this.infos.name}}</h2>
		<div class="activeity-time">时间：{{this.infos.activeTime}}</div>
		<p class="activeity-nr">社团：{{this.infos.teamName}} <br>要求：{{this.infos.ask}} <br>概述：{{this.infos.comm}} <br>详情：{{this.infos.detail}}</p>
		<button class="activeity-bm">报名</button>
	</div>
</template>

<script>
	import {
		getManTeamList,
		getLoginUser,
		getActiveLogs,
		getPageActivities
	} from "../../api";
	
	export default {
	
		data() {
	
			return {
				infos: "",
				teams: [],
				userType: "",
				activeLogs: [],
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
					activeName: "",
				},
				activitiesForm: {
					id: "",
					name: "",
					comm: "",
					detail: "",
					ask: "",
					total: 1,
					activeTime: "",
					teamId: "",
				}
			}
		},
		methods: {
	
			getActivePeople(activeId){
	
				getActiveLogs(activeId).then(resp =>{
					
					this.activeLogs = [];
					this.activeLogs = resp.data;
				});
			},
	
			getPageInfo(pageIndex, pageSize) {
	
				getPageActivities(pageIndex, pageSize, this.qryForm.token).then(resp => {
	
					this.pageInfos = resp.data.data;
					this.pageIndex = resp.data.pageIndex;
					this.pageSize = resp.data.pageSize;
					this.pageTotal = resp.data.pageTotal;
					this.totalInfo = resp.data.count;
	
					this.loading = false;
					for(let i = 0; i < this.pageInfos.length; i++){
						if(this.pageInfos[i].id == this.$route.query.id){
							this.infos = this.pageInfos[i]
						}
					}
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
		}
	}
</script>

<style>
	.activeity-h2 {
	    width: 1200px;
	    height: 82px;
	    font-size: 32px;
	    text-align: center;
	    line-height: 82px;
	    display: block;
	    margin: 0 auto;
	}
	
	.activeity-time {
	    width: 1200px;
	    height: 55px;
	    text-align: center;
	    line-height: 55px;
	    border-bottom: 1px dashed #d5d5d5;
	    margin: 0 auto;
	}
	
	.activeity-nr {
	    width: 1200px;
	    height: 80px;
	    text-indent:2em;
	    margin: 30px auto;
	}
	
	.activeity-bm {
	    width: 80px;
	    height: 40px;
	    color: #fff;
	    background-color: #fa730d;
	    border-radius: 10px;
	    border: none;
	    position: relative;
	    top: 30px;
	    left: 1280px;
	}
</style>