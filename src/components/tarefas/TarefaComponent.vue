<template>
    <div>
        <v-list-item
            :class="{'light-blue lighten-5':tarefa.concluido}"
            @click="changeValue()"
        >
            <template v-slot:default="{}">
                <v-list-item-action>
                    <v-checkbox :input-value="tarefa.concluido"></v-checkbox>
                </v-list-item-action>

                <v-list-item-content>
                    <v-list-item-title
                        :class="{'text-decoration-line-through': tarefa.concluido}"
                    >{{tarefa.titulo}}</v-list-item-title>
                </v-list-item-content>

                <v-list-item-action>
                <v-btn 
                    icon
                    @click.stop="handleRemoveTarefa(tarefa.id)"
                >
                    <v-icon color="red darken-3">mdi-delete-forever</v-icon>
                </v-btn>
                </v-list-item-action>

            </template>
        </v-list-item>
        <v-divider></v-divider>
    </div>
</template>

<script>
    export default {
        props:['tarefa'],
        data(){
            return{
                tarefaRes:this.tarefa
            }
        },
        methods:{
            changeValue(){
                this.tarefaRes.concluido = !this.tarefaRes.concluido
            },
            handleRemoveTarefa(id){
                this.$store.commit('removeTarefa', id)
            }
        }
    }
</script>

<style>

</style>