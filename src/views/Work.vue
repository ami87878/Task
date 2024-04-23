<template>
  

<div class="pa-4">

         <v-text-field
            type="text"
            @keyup.enter="addUserInput"
            @click:append-outer="addUserInput"
            v-model="userInput"
            outlined
            label="Please add your Task"
            append-outer-icon="mdi-plus"
            clearable
          ></v-text-field>

          
          <!-- modal -->

                  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      persistent
      max-width="300"
    >
      
      <v-card>
        <v-card-title class="text-h6">
         You should write task !
        </v-card-title>
        <v-card-text>

            for submit your task in todo list you should write task and the task must not be empty

        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
         
          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Agree
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>

          <!-- modal -->
          
  <v-list
      
      
      flat
    >
 

        <v-list-item :class="{'green accent-2 ':item.done}" v-for="item in works" :key="item.id" @click="item.done=!item.done">
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="item.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content >
              <v-list-item-title :class="{'text-decoration-line-through':item.done}" >{{ item.title }}</v-list-item-title>
              <v-divider :key="item.id" ></v-divider>
              
            </v-list-item-content>
            <v-list-item-action >

              <v-btn icon color="teal" @click.stop="deleteFunc($event,item.id)">
                       <v-icon >mdi-delete</v-icon>
            </v-btn>

            </v-list-item-action>
          </template>
        </v-list-item>
      
    </v-list>
  
</div>

</template>

<script>
  

  export default {
    name: 'Work',

    data(){

      return{

        dialog:false,
        userInput:'',
        works:[

        {

          id:1,
          done:false,
          title:'practice code'


        },
        {

          id:2,
          done:false,
          title:'work out'


        },
        {

          id:3,
          done:false,
          title:'yoga'


        },

        ],



      }

    },

    methods:{
    

      deleteFunc(e,id){
      
        this.works=this.works.filter((item)=>item.id!==id)

      
      
      },


      addUserInput(){

          
      if(this.userInput.trim()!==''){

        this.works.push(
          
        {
            id:Date().slice(Date().lastIndexOf(':')+1,Date().lastIndexOf(':')+3),
            
            title:this.userInput,

            done:false
          
          }
          
          );

          console.log(Date().slice(Date().lastIndexOf(':')+1,Date().lastIndexOf(':')+3))
            

      }

      else{


          this.dialog=true


      }
    
    
      this.userInput=''
    
    }
  }
}
    
  
</script>
