<template>
    <div class="container mt-5">
	<form class="row justify-content-center" v-on:submit.prevent="signIn">
	  <div class="col-md-6">
	    <h1 class="h3 mb-3 font-weight-normal">請先登入</h1>
        
	    <div class="mb-2">
	      <label for="inputEmail" class="sr-only">Email address</label>
	      <input
	        type="email"
	        id="inputEmail"
	        placeholder="Email address"
	        required
	        autofocus
            class="form-control"
            v-model="user.username"
	      />
	    </div>

	    <div class="mb-2">
	      <label for="inputPassword" class="sr-only">Password</label>
	      <input
	        type="password"
	        id="inputPassword"
	        class="form-control"
	        placeholder="Password"
	        required
            v-model="user.password"
	      />
	    </div>
	
	    <div class="text-end mt-4">
	      <button class="btn btn-lg btn-primary btn-block" type="submit">登入</button>
	    </div>
	  </div>
	</form>
</div>
</template>












<script>


export default {
    data:function(){
        return{
            user:{
                username:'',
                password:'',
            },
        };
    },
	// methods:{
	// 	signIn:function(){
	// 		const api=`${process.env.VUE_APP_API}/admin/signin`;
	// 		// console.log(api);
	// 		this.$http.post(api,this.user).then((res)=>{
				
	// 			const {token,expired}=res.data;
	// 			// const token=res.data.token;
	// 			// const expired=res.data.expired;

	// 			// console.log(token,expired);

	// 			document.cookie=`hexToken=${token};expires=${new Date(expired)}`
				
	// 			console.log(res);

				
	// 			});
	// 	},
	// },

	methods:{
		signIn:function(){
			const api=`${process.env.VUE_APP_API}/admin/signin`;
			// console.log(api);
			this.$http.post(api,this.user).then((res)=>{
				
				if (res.data.success) {

            	const { token, expired } = res.data;

            	document.cookie = `hexToken=${token}; expires=${new Date(expired)}`;
				
            	this.$router.push('/dashboard');
          		}
			});
		},
	},
}






</script>



