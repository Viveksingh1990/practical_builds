Email Modal
===========

For the starting code for this lesson, switch to branch: [https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-start](https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-start)

Opening the email below the mail table is a good proof of concept, but it’s not ideal - especially as the number of emails grows. Much better is to open it up in a modal.

We’ll create a generic Modal component

    <!-- ModalView.vue template -->
    <div class="modal">
      <div class="overlay"></div>
      <div class="modal-card">
        <slot />
      </div>
    </div>
    

Then we’ll wrap it around the MailView component. Be sure to import and register the component.

    <ModalView v-if="openedEmail">
      <MailView :email="openedEmail" />
    </ModalView>
    

This will open up the modal whenever we click on an email.

![https://firebasestorage.googleapis.com/v0/b/vue-mastery.appspot.com/o/flamelink%2Fmedia%2F6_1.jpg?alt=media&token=a8c29dfb-c231-4dac-bbe6-b15e8ae80dbd](https://firebasestorage.googleapis.com/v0/b/vue-mastery.appspot.com/o/flamelink%2Fmedia%2F6_1.jpg?alt=media&token=a8c29dfb-c231-4dac-bbe6-b15e8ae80dbd)

Next we want to be able to close our modal.

This is accomplished by emitting an event whenever we click on the overlay.

    <template>
      <div class="modal">
        <div class="overlay" @click="emit('closeModal')"></div>
        <div class="modal-card">
          <slot />
        </div>
      </div>
    </template>
    
    <script>
      export default {
        setup(props, {emit}) {
          return { 
    	emit
          }
        }
      }
    </script>
    

    <ModalView v-if="openedEmail" @closeModal="openedEmail = null">
      <MailView :email="openedEmail" />
    </ModalView>
    

The emitted event will trigger the code in our ModalView declaration, and the openedEmail will be set to null.

For the ending code for this lesson, switch to branch: [https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-end](https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-end)

### Lesson Resources

##### Source Code:

*   [Starting Code](https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-start)
    
*   [Ending Code](https://github.com/Code-Pop/build-gmail-clone-with-vue-3/tree/video-6-end)
