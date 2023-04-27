<template>
    <div>
        <h1> This is profile page </h1>
        <button @click="logout"> logout </button>
    </div>
    

</template>

<script>
export default {
//   middleware ({ app, redirect }) {
//     if (process.client && !localStorage.getItem('token')) {
//     return redirect('/login')
//   }

//   return app.$axios.$get('/profile').then((token) => {
//     // If the user is not authenticated, redirect to login page
//     if (!token) {
//       return redirect('/login')
//     }
 
//     // If the user is authenticated, proceed to the next middleware or the page itself
//     return Promise.resolve()
//   })
// },
methods:{
        logout(){
            if(localStorage){
              localStorage.clear()
            } 
        }
    }
}



    // middleware ({ store, redirect }) {
    // // Check if the user is authenticated
    // const token = process.server?'true':!!localStorage.getItem('token') 
    //   // doubt. find new ways to access local storgae
    //   console.log(token, "i ran")
    // if (!token) {
        
    //   return redirect('/login')
    // }
  // },
    
    


</script>

<style>

</style>
