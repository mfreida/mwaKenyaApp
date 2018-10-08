  <template>
        <div class="page">
            <div v-if="page">
                <label for="title">Title</label>
                <input type="text" v-model="page.title" class="title" name="title" placeholder="Enter a title" />
                <label for="content">Content</label>
                <textarea class="content" name="content" v-model="page.content" placeholder="Enter some content"></textarea>
                <button id="deleteBtn" @click="deletePage()">Delete Page</button>
                <button id="saveBtn"  @click="savePage()">Save Page</button>
            </div>
            <div v-else>
                <h1>&larr; Create a new page "New Page +" to get started!</h1>
            </div>
        </div>
    </template>
    <script>

    const surix = Surix.Service.init();
    const requests = Surix.requests;

      export default {
        name: 'Page',
        props: ['page'],
        methods: {
          deletePage () {
            this.$emit('delete-page')
          },
          savePage () {
            this.$emit('save-page')
          }
        }
      }
    </script>

    <style scoped>
        .page {
            width: 100%;
            padding: 2rem;
            box-shadow: 3rem 0 5rem 3rem #62d1bf;
        }

        .content, .title {
            border-style: none;
            border-radius: 0.25rem;
            border: solid 1px lightgray;
            width: 100%;
            box-sizing: border-box;
            margin-bottom: 1.25rem;
        }

        .content:focus, .title:focus {
            outline: 0;
        }

        .content {
            font-family: 'Avenir', Helvetica, Arial, sans-serif;
            resize: vertical;
            font-size: 1.5rem;
            padding: 0.5rem;
            height: 20rem;
        }

        .title {
            font-size: 2rem;
            padding: 0.5rem 1rem;
        }

        label {
            margin-bottom: 0.5rem;
            display: inline-block;
        }

        button {
            border-style: none;
            padding: 0.5rem 0.75rem;
            background-color: #44c384;
            margin-right: 1rem;
            border-radius: 0.25rem;
            color: rgb(14, 1, 1);
            font-size: 1rem;
            cursor: pointer;
        }

        button:hover {
            background-color: #368ea2;
        }
    </style>