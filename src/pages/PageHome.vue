<template>
  <q-page>
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

 <q-list
 >
      <q-item class="q-py-md">
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
            </span>
          </q-item-label>
          <q-item-label class="qweet-content text-body1">
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. At maxime quis corporis provident laborum veritatis! Quia ex voluptatem, id provident voluptas nemo
             accusantium, nihil suscipit corrupti laboriosam expedita a maiores.
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
             />
          </div>
        </q-item-section>

        <q-item-section side top>
          1 min ago
        </q-item-section>
      </q-item>


    </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageHome',
  data(){
    return {
      newQweetContent: ''
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
