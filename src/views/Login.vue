<template>
  <div
    class="margin-b-25"
  >
<!-- 
  <div v-for="(utilisateur, index) in utilisateurs">
	{{ index }} - {{ utilisateur.nom }}
   </div> -->

   <p  v-if="st==true">
     &copy;2020 Acme Corp
   </p>
   <p v-else>
    fghjk
   </p>

   <input v-model="nome" type="text" placeholder="nom" />
  
  {{nome}}
    <!-- {{count}} -->
  <Form :attribut="returnValue()" />
  </div>
</template>

<script>
import { defineComponent,ref,onBeforeMount,onMounted } from "vue";
import Form from  '../components/login/Form.vue';
export default defineComponent({
  name: "login",
  components: {
    Form
  },
  props: {},
  setup() {
    const st=false;

    const count=ref(0);
    const countNotRef=10;

    const nome= ref("amina");

    onBeforeMount(()=>{
      console.log("onBeforeMount")
    })
    onMounted(()=>{
      console.log("onMounted")
    })

    const utilisateurs=[

      {nom: "rafik"},
      {nom: "amina"}

    ]

    const copyrating = "&copy;2020 Acme Corp. All rights reserved."
    const returnValue=()=>{
       return count.value
    }


    return {
      returnValue,
      count,
      utilisateurs,
      nome,
      st
      
    };
  },
});
</script>
