<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        create-nuxt-demo
        --{{links && links.length || "undefined"}}--
      </h1>
      <div class="links">
        <a
          v-for="(link,index) in links"
          :key="index"
          href="javascript:void(0);"
          rel="noopener noreferrer"
          class="button--grey"
        >
          {{link}}
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted(){
    this.loadLinks().then(data =>{
       this.links = data.links;
    });
  },
  methods: {
    loadLinks(){

      return new Promise((resolve,reject) =>{

        setTimeout(() => {
          var links = { links: ["傻", "逼"] };
          resolve(links)
        }, 500);

      });

    }
  },
  asyncData(context){
    var links = { links: ["你", "好"] };
    return new Promise((resolve, reject) =>{
        setTimeout(() => {
          resolve(links);
        }, 500);

    }).then((res) => {
       return res;
    });
    // return links;
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
