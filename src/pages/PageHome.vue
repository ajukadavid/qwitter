<template>
  <q-page class="relative-position">
        <q-scroll-area class="absolute fullscreen">

    <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
      <div class="col">
           <q-input
      autogrow
       bottom-slots
       class="new-qweet"
        v-model="newQweetContent"
        placeholder="What's happening"
        counter maxlength="280"
        >
      <template v-slot:before>
        <q-avatar size="xl">
          <img src="https://s.gravatar.com/avatar/d44fdfe34fc3905a5fb25613aa07c4a2?s=80" />
        </q-avatar>
      </template>


    </q-input>
      </div>
      <div class="col col-shrink">
        <q-btn
        @click="addNewQweet"
         color="primary"
         label="Qweet"
         rounded
         unelevated
         no-caps
         class="q-mb-lg"
        :disable="!newQweetContent"
         />
      </div>

    </div>
 <q-separator
 size="10px"
 color="grey-2"
 class="divider"
 />

 <q-list separator>
      <transition-group
  appear
  enter-active-class="animated fadeIn slow"
  leave-active-class="animated fadeOut slow"
>

      <q-item
      v-for="qweet in qweets"
      :key="qweet.date"
       class="q-py-md"
       >
        <q-item-section avatar top>
          <q-avatar>
            <img src="https://s.gravatar.com/avatar/d44fdfe34fc3905a5fb25613aa07c4a2?s=80">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label class="text-subtitle1">
            <strong>
              Ajuka David
            </strong>
            <span class="text-grey-7">
              @elderajuka
             <br class="lt-md"> &bull;  {{relativeDate(qweet.date)}}
            </span>
          </q-item-label>
          <q-item-label class="qweet-content text-body1">
           {{qweet.content}}
           </q-item-label>
          <div class="row qweet-icons justify-between q-mt-sm">
            <q-btn
            color="grey"
            icon="far fa-comment"
            flat
            size="sm"
            round
             />
             <q-btn
            color="grey"
            icon="fas fa-retweet"
            flat
            size="sm"
            round
             />
             <q-btn
            color="grey"
            icon="far fa-heart"
            flat
            size="sm"
            round
             />
             <q-btn
            color="grey"
            icon="fas fa-trash"
            flat
            size="sm"
            round
            @click="deleteQweet(qweet)"
             />
          </div>
        </q-item-section>

      </q-item>
</transition-group>
    </q-list>
    </q-scroll-area>
  </q-page>
</template>

<script>
import { formatDistance } from 'date-fns'

import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageHome',
  data(){
    return {
      newQweetContent: '',
      qweets: [
        {
          content: `
        When we have respect for ourselves and others, we gravitate towards connections that encourage that
          `,
          date: 1646082317300
        },
         {
          content: `
          Anger is the ultimate destroyer of your own peace of mind
          `,
          date: 1646082356035
        }
      ]
    }
  },
  methods: {
    relativeDate(value) {
      return formatDistance(value, new Date())
    },
    addNewQweet(){
     let newQweet = {
       content: this.newQweetContent,
       date: Date.now()
     }
     this.qweets.unshift(newQweet)
     this.newQweetContent = ''
    },
    deleteQweet(qweet){
      let dateToDelete = qweet.date
      let index = this.qweets.findIndex(qweet => qweet.date === dateToDelete)
      this.qweets.splice(index, 1)
    }
  }
})
</script>


<style lang="sass">
.new-qweet
  textarea
      font-size: 19px
      line-height: 1.4 !important

.divider
  border-top: 1px solid
  border-bottom: 1px solid
  border-color: $grey-4


.qweet-content
  white-space: pre-line


.qweet-icons
  margin-left: -5px
</style>
