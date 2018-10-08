 <template>
      <div id="app">
          <Notebook @change-page="changePage" @new-page="newPage" :pages="pages" :activePage="index" />
          <Page @save-page="savePage" @delete-page="deletePage" :page="pages[index]" />
      </div>
    </template>

    <script>
    import Notebook from './components/Notebook'
    import Page from './components/Page'

    const service = Surix.Service.init();
    const requests = Surix.requests;


    export default {

      name: 'app',
      components: {
        Notebook,
        Page
      },
      data: () => ({
        pages: [],
        index: 0
      }),

      methods: {
        anotherPage (enity) {
          const entity = {
            this:pages.push({
            title: '',
            content: ''
          }),
           surix:request(requests.data.createEntity, entity)
            .then((createdEntity) => {
                title.value = '';
                content.value = '';
            })
            .catch(error => {
                console.error('Error occurred', error);
            })
          }
        },
      this:index = this.pages.length - 1},

      //creating a new page
          

       /* newPage () { 
          const entity = {}

          this.pages.push({
            title: '',
            content: ''
          })
          this.index = this.pages.length - 1
        },
        */
        //changing a page
        changePage (index) {
          this.index = index
        },
        //saving a page
        savePage () {
           // nothing as of yet
        },
        //deleting a page
        deletePage () {
          this.pages.splice(this.index, 1)
          this.index = Math.max(this.index - 1, 0)
        }
      }
    
    //removed a curly bracket
    </script>

    <style>
    html, body, #app {
        height: 100%;
    }
    body {
        margin: 0;
    }
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        display: flex;
        flex-direction: row;
    }
    </style>