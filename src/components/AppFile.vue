<template>
    <div class=" flex items-center justify-between border-b-2 border-gray-100">
        <div class="flex py-3 text-sm overflow-ellipsis w-6/12">
            {{file.name}}
        </div>
        <div class="flex items-center">
            <a href="" class=" inline-block text-sm p-3 text-indigo-700 font-medium">Get Sharable Link</a>
            <a href="" class=" inline-block text-sm p-3 text-pink-500 font-medium">Delte</a>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        file: {
            required: true,
            type: Object
        }
    }
}
</script>

<style>

</style>