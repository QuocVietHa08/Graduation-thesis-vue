<template>
  <div class="contacts-container">
    <h1>Contacts</h1>
    <!-- component -->
    <div class="contacts-form-wrapper">
      <div class="contacts-text">
        hello
      </div>
      <div class="contacts-form">
        <form class="w-full max-w-lg">
          <div class="flex flex-wrap -mx-3 mb-6">
            <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
              <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="grid-first-name"
              >
                First Name
              </label>
              <input
                class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"
                id="grid-first-name"
                type="text"
                placeholder="Enter your firt name"
              />
            </div>
            <div class="w-full md:w-1/2 px-3">
              <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="grid-last-name"
              >
                Last Name
              </label>
              <input
                class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                id="grid-last-name"
                type="text"
                placeholder="Enter your last name"
              />
            </div>
          </div>
          <div class="flex flex-wrap -mx-3 mb-6">
            <div class="w-full px-3">
              <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="grid-password"
              >
                E-mail
              </label>
              <input
                class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                id="email"
                type="email"
                placeholder="Enter your email"
              />
            </div>
          </div>
          <div class="flex flex-wrap -mx-3 mb-6">
            <div class="w-full px-3">
              <label
                class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                for="grid-password"
              >
                Message
              </label>
              <textarea
                class=" no-resize appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500 h-48 resize-none"
                id="message"
                placeholder="Enter your message"
              ></textarea>
            </div>
          </div>
          <div class="md:flex md:items-center">
            <div class="md:w-1/3">
              <button
                class="shadow button-submit-form focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded"
                type="button"
              >
                Get in touch 
              </button>
            </div>
            <div class="md:w-2/3"></div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
// import MapBoxComponent from '../../components/mapbox/Mapbox.vue'

export default {
  name: "index"
  // component: {
  //   MapBoxComponent
  // }
};
</script>
<style scoped lang="scss">
.contacts-container {
  width: 100%;
  height: 100vh;

  h1 {
    padding-top: 40px;
    font-size: 50px;
    text-align: center;
  }
}


.contacts-form-wrapper {
  width: 100%;
  height: auto;  
  display: flex;
  padding: 20px 0px;
  
  .contacts-text {
    width: 50%;
    display: flex;
    justify-content: center;
  }

  .contacts-form {
    width: 50%;
    display: flex;
    justify-content: center;
  }
}

.button-submit-form {
  background-color: #9cbf10;
  padding: 10px 30px;
  border-radius: 25px;
}
</style>
