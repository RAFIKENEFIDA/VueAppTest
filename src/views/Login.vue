<template>
  <div class="w-full max-w-xs">
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="username"
        >
          Nom
        </label>
        <input
          v-model="formData.nom"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="username"
          type="text"
          placeholder="Username"
        />
      </div>
      <div class="mb-4">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="username"
        >
          Prenom
        </label>
        <input
          v-model="formData.prenom"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="username"
          type="text"
          placeholder="Username"
        />
      </div>
      <div class="mb-4">
        <label
          class="block text-gray-700 text-sm font-bold mb-2"
          for="username"
        >
          Tel
        </label>
        <input
          v-model="formData.tel"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="username"
          type="text"
          placeholder="Username"
        />
      </div>

      <div class="flex items-center justify-between">
        <button
          @click="resgisterUser()"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="button"
        >
          Register
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "login",
  components: {},
  props: {},
  setup() {
    const formData = ref({
      nom: "",
      prenom: "",
      tel: "",
    });



    const  resgisterUser =  async() => {
       var myHeaders = new Headers();
        myHeaders.append("Accept", "application/json");
        myHeaders.append("Content-Type", "application/json");

      
        var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: formData,
          redirect: 'follow'
        };

       await fetch("http://localhost/Brief6/apiUser/creatUser", requestOptions)
        .then(response => response.json())
        .then((response)=>{
          console.log(response)
        })
    ;
    };

    return {
      formData,
      resgisterUser,
    };
  },
});
</script>
