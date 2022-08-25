# PaginaComments_Vue
PaginaComments_Vue
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      rel="stylesheet"
      href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css"
      integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO"
      crossorigin="anonymous"
    />

    <title>Document</title>
  </head>
  <body>
    <div id="app"></div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>

    <script>
      new Vue({
        // render: (h) => h("div", this.hi),
        el: "#app",
        template: `
        <div class="container">
             <h1>Comentários</h1>
             <hr/>
            <div class="form-todo form-group">    
                <p>
                    <input type="text" class="form-control" placeholder="nome" name="author" v-model="name">
                </p>
                <p>
                    <textarea class="form-control" placeholder="Comentario" name="message" v-model="message"></textarea>
                </p>
                <button v-on:click = "addComment" type="submit" class="btn btn-primary">Comentar</button>
            </div>
            <div class="list-group">
                <div class="list-group-item" v-for="(comment, index) in allComments">
                    <span class="comment__author">Autor: <strong> {{ comment.name }}</strong> </span>
                    <p>{{ comment.message }}</p>
                    <div>
                        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                    </div>
                </div>
            </div>
            <hr/>
        </div>
`,
        data() {
          return {
            comments: [],
            name: "",
            message: "",
          };
          // };
        },
        methods: {
          addComment() {
            // if (this.name.trim() === "" || this.message.trim() === "") {
            if (this.message.trim() === "") {
              return;
            }
            // console.log("Chamado");
            // console.log(this.name);
            // console.log(this.message);
            this.comments.push({
              name: this.name,
              message: this.message,
            });
            this.name = "";
            this.message = "";
          },
          removeComment(index) {
            // console.log(index);
            this.comments.splice(index, 1);
          },
          //   },
        },
        computed: {
          allComments() {
            return this.comments.map(comment => ({
              ...comment,
              name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
          }
        },
        watch:{
            comments(val){
                console.log('val', val)
            }
        }
      })
    </script>
    <!-- <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script> -->
  </body>
</html>

<!-- https://www.youtube.com/watch?v=cSa-SMVMGsE&t=513s -->
