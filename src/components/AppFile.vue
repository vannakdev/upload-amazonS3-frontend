<template>
    <div class=" flex items-center justify-between border-b-2 border-gray-100">
        <div class="flex py-3 text-sm overflow-ellipsis w-6/12">
            {{file.name}}
        </div>
        <div class="flex items-center">
            <a href="" class=" inline-block text-sm p-3 text-indigo-700 font-medium">Get Sharable Link</a>
            <a href="" class=" inline-block text-sm p-3 text-pink-500 font-medium" @click.prevent="DeleteFile">Delte</a>
        </div>
    </div>
</template>

<script>
import {mapActions } from 'vuex'
export default {
    props:{
        file: {
            required: true,
            type: Object
        }
    },
    methods:{
        ...mapActions({
            DeleteFileAction: 'files/deleteFile'
        }),
        DeleteFile(){
            if(window.confirm('Really Delete this file ?')){
                this.DeleteFileAction(this.file.uuid)
            }
        }
    }
}
</script>

<style>

</style>