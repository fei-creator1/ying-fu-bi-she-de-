<template>
	<div>
	  <h2>评论页面</h2>
	  <el-form :model="form" label-width="80px">
		<el-form-item label="用户名">
		  <el-input v-model="form.username"></el-input>
		</el-form-item>
		<el-form-item label="评论内容">
		  <el-input type="textarea" v-model="form.comment"></el-input>
		</el-form-item>
		<el-form-item>
		  <el-button type="primary" @click="submitForm">提交评论</el-button>
		  <el-button @click="resetForm">重置表单</el-button>
		</el-form-item>
	  </el-form>
	  <div class="comments">
		<h3>最新评论</h3>
		<ul>
		  <li v-for="(comment, index) in comments" :key="index">
			<span class="username">{{ comment.username }}:</span>
			<span class="comment">{{ comment.comment }}</span>
		  </li>
		</ul>
	  </div>
	</div>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		form: {
		  username: '',
		  comment: ''
		},
		comments: []
	  }
	},
	methods: {
	  submitForm() {
		// 将表单数据加入到评论数组中
		this.comments.unshift({
		  username: this.form.username,
		  comment: this.form.comment
		});
		// 重置表单
		this.resetForm();
	  },
	  resetForm() {
		this.form.username = '';
		this.form.comment = '';
	  }
	}
  }
  </script>
  
  <style scoped>
  .comments {
	margin-top: 30px;
  }
  
  .username {
	font-weight: bold;
  }
  
  .comment {
	margin-left: 10px;
  }
  </style>