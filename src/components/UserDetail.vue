<template>
    <div class="col-md-6">
        <h3>Child Component 1</h3>
        <p>Ben User.vue isimli Parent component'in içerisinde ki bir child componentim</p>
        <p>Kullanıcı adı artık : {{name}}</p>
        <p>Kullanıcı adı : {{switchName()}}</p>
        <p>Kullanıcı Yaşı : {{age}}</p>
        <button @click="sendToParent">Veriyi Parent'a Gönder</button>
    </div>
</template>
<script>
    import  { eventBus }  from '../main';
    export default{
        props : {
        name : {
            type : String,
            required : true,
            default : "videosinif.com",
        },
        age : String
    },
        methods : {
            switchName(){
                return this.name.split("").reverse().join("")
            },
            sendToParent(){
                this.$emit("data","Doğukan Çelik");
            }
        },
        created(){
          eventBus.$on("ageWasEdited", (age) => {
              this.age=age;
          })
        }
    }

</script>

<style scoped>
div {
    background-color: lightcoral;
    padding: 20px;
    border: 1px solid #666;
    display: inline-block;
   }
</style>