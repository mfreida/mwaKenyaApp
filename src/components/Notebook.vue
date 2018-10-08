 <template>
        <div class="notebook">
            <ul>
                <li v-for="(page, index) of pages" class="page" :key="index" :class="{ 'active': index === activePage }" @click="changePage(index)">
                    <div>{{page.title}}</div>
                </li>
                <li id="NewPage" class="new-page" @click="newPage()">New Page +</li>
            </ul>
        </div>
    </template>

    <script>
      export default {
        name: 'Notebook',
        props: ['pages', 'activePage'],
        methods: {
          changePage (index) {
            this.$emit('change-page', index)
          },
          newPage () {
            this.$emit('new-page')
          }
        }
      }
    </script>

    <style scoped>
        .notebook {
            max-width: 20rem;
            width: 30rem;
            background: #ecfcff;
        }

        ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            height: 100%;
            position: relative;
        }

        li {
            padding: 1rem;
            font-size: 1.25rem;
            min-height: 1.5rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        li:hover {
            cursor: pointer;
            background-color: #f5c5e7;
        }

        .active {
            background-color: #1215c2;
        }

        .active:hover {
            background-color: #c15cab;
        }

        .new-page {
            background-color: #5b235d;
            color: white;
            position: absolute;
            bottom: 0;
            width: 100%;
            box-sizing: border-box;
        }

        .new-page:hover {
            background-color: #181d48;
        }
    </style>