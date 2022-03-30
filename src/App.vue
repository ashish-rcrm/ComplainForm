<template>
  <div class="container box one">
    
    <form action="">
      <div class="row">
        <div class="column">
          <h1 class="title is-2">File a Complain</h1>
          <hr class="is-divider">

          <div class="field">
            <label for="name" class="label">Name</label>
            <div class="control has-icons-left">
              <input 
                      type="text" 
                      id="name"
                      class="input"
                      v-model="userData.name">
                <span class="icon is-small is-left">
                  <i class="fas fa-user"></i>
                </span>
            </div>
          </div>
          <div class="field">
            <label for="email" class="label">E-mail</label>
            <div class="control has-icons-left">
              <input 
                      type="email"
                      name="" 
                      id="email" 
                      class="input"
                      v-model="userData.email">
              <span class="icon is-small is-left">
                <i class="fas fa-envelope"></i>
              </span>
            </div>
          </div>
          <div class="field">
            <label for="pass" class="label">Password</label>
            <div class="control has-icons-left">
              <input 
                      type="password" 
                      id="pass" 
                      class="input"
                      v-model="userData.password">
              <span class="icon is-small is-left">
                <i class="fas fa-lock"></i>
              </span>
            </div>
          </div>
          <div class="field">
            <label for="age" class="label">Age</label>
            <div class="control has-icons-left">
              <input 
                      type="number" 
                      name="" 
                      id="age" 
                      class="input"
                      v-model="userData.age">
              <span class="icon is-small is-left">
                <i class=""></i>
              </span>
            </div>
          </div>
          <div class="field">
            <label for="data" class="label">Message</label>
            <div class="control">
              <textarea 
                        class="textarea is-primary" 
                        id="data" 
                        cols="100" 
                        rows="4"
                        v-model="message">

              </textarea>
            </div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label for="" class="label">Options</label>
          <div class="field">
            <label for="sendmail" class="checkbox">
              <input 
                      type="checkbox" 
                      id="sendmail"
                      value="sendMail"
                      v-model="options">Sendmail
            </label>
          </div>
          <div class="field">
            <label for="hardcopy" class="checkbox">
              <input 
                      type="checkbox" 
                      id="hardcopy"
                      value="hardcopy"
                      v-model="options">Hardcopy
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label for="" class="label">Gender</label>
          <div class="control">
            <label for="male" class="radio">
            <input 
                    type="radio" 
                    value="Male" 
                    id="male"
                    v-model="gender">Male
          </label>
          <label for="female" class="radio">
            <input 
                    type="radio" 
                    value="Female" 
                    id="female"
                    v-model="gender">Female
          </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label for="priority" class="label">Priority</label>
          <div class="select is-rounded is-primary">
            <select 
                    id="priority"
                    v-model="selectedPriority">
              <option 
                      v-for="priority in priorities" 
                      :key="priority"
                      :selected="priority == 'Medium'">{{priority}}</option>
            </select>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label for="file" class="label">Upload File</label>
          <div class="file">
            <label class="file-label">
              <input 
                      class="file-input"
                      type="file" 
                      @change="fileSelected">
              <span class="file-cta">
                <span class="file-icon">
                  <i class="fas fa-upload"></i>
                </span>
                <span class="file-label">
                  Choose a file…
                </span>
              </span>
            </label>
          </div>
        </div>
      </div>
      <hr>
      <div class="row">
        <div class="column">
          <button 
                  class="button is-primary"
                  @click.prevent="submitted()">Submit</button>
        </div>
      </div>
    </form>
    
    <div class="row" v-if="isSubmitted">
      <hr>
      <div class="colum">
        <div class="panel">
          
            <p class="panel-heading">Your Data<p>

          <div class="panel-body">
            <p class="panel-block">Name<pre class="space">    </pre>: <strong class="temp">{{userData.name}}</strong></p>
            <p class="panel-block">Email<pre class="space">    </pre>: <strong class="temp">{{userData.email}}</strong></p>
            <p class="panel-block">Password<pre class="space"> </pre>: <strong class="temp">{{userData.password}}</strong></p>
            <p class="panel-block">Age<pre class="space">      </pre>: <strong class="temp">{{userData.age}}</strong></p>
            <p style="white-space : pre" class="panel-block">Message<pre class="space">  </pre>: <strong class="temp">{{message}}</strong></p>
            <div class="panel-block">
              <p >Options </p>
                <div class="temp">
                  
                  <ul>
                    <li v-for="option in options" :key="option">
                      <strong><strong>{{ option }}</strong></strong>
                    </li>
                  </ul>
                </div>
            </div>
            <p class="panel-block">Gender<pre class="space">   </pre>: <strong class="temp">{{gender}}</strong></p>
            <p class="panel-block">Priority<pre class="space">   </pre>: <strong class="temp">{{selectedPriority}}</strong></p>
            <p class="panel-block">File Upload Name: <strong class="temp">{{selectedFile}}</strong></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      userData : {
        name : "",
        email : "",
        password : "",
        age : 0
      },
      message : "A Text",
      options : [],
      gender : "Male",
      selectedPriority : "Medium",
      priorities : ["High", "Medium", "Low"],
      selectedFile : null,
      isSubmitted : false
    }
  },
  methods : {
    submitted(){
      this.isSubmitted = true;
    },
    fileSelected(){
      this.selectedFile = event.target.files[0].name;
    }
  }
}
</script>

<style scoped>
  .one{
    width : 50%
  }
  .temp{
    padding-left: 1rem;
  }
  .addWidth{
    width: 100%;
  }
  .space{
    background-color: white;
    padding : 0;
  }
</style>
