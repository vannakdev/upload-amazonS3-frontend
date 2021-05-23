<template>
  <div class="px-80">
    <div class="mb-8">UPLOAD</div>
    <div class=" font-medium pb-3 border-b-2 border-gray-200 text-gray-800">
     <app-uploader  @onprocessfile="storeFile"/>
    </div>
    <template v-if="files.length">
      <AppFile v-for="file in files" :key="file.uuid" :file="file"/>
    </template>
    <p v-else>Tthere are no file here  right now</p>
  </div>
</template>

<script>
import axios from 'axios'
import AppUploader from '@/components/AppUploader'
import AppFile from '@/components/AppFile'
import { mapGetters, mapActions, mapMutations } from 'vuex'
export default {
  name: "Upload",
  components: {
    AppUploader,
    AppFile
  },
  mounted(){
    this.getFilesAction()
  },
  computed: {
    ...mapGetters({
      files: 'files/files'
    })
  },
  methods:{
    ...mapActions({
      getFilesAction: 'files/getFiles'
    }),
    ...mapMutations({
      addFile: 'files/ADD_FILE'
    }),
    async storeFile(file){
      let response = await axios.post('/api/files',{
        name: file.filename,
        size: file.fileSize,
        path: file.serverId
      })

      this.addFile(response.data.data)
    }
  }
};
</script>
