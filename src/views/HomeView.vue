<template>
  <div class="container mt-5">
    <div clas="row">
      <div class="home col-12">
        <h2>Información de Teclado <strong>Casio: CT-S400</strong></h2>
        <img :src="data.image" class="keyboard-dim"/>
      </div>
      <div class="col-12 mt-5">
        <hr>
        <div class="row mt-5">
          <div class="col-md-4 col-sm-12">
            <button class="btn btn-primary btn-lg" @click="showInfo('video')">Video presentación</button>
          </div>
          <div class="col-md-4 col-sm-12">
            <button class="btn btn-primary btn-lg" @click="showInfo('audio')">Audios de pruebas</button>
          </div>
          <div class="col-md-4 col-sm-12">
            <button class="btn btn-primary btn-lg" @click="showInfo('document')">Ficha técnica</button>
          </div>
        </div>
      </div>
      <div class="col-12">
        <div class="mt-5 mb-5" v-if="showVideo">
          <iframe width="560" height="315" :src="data.video" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
        <div class="mt-5 mb-5" v-if="showAudio">
          <div class="p-2 px-3 pt-2" style="border: 1px solid" v-for="(audio, index) in data.audios" :key="index">
            <iframe style="width: 100%;" height="20" :src="audio" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
          </div>
        </div>
        <div class="mt-5 mb-5" v-if="showDocument">
          <iframe style="width: 70%; height: 450px" :src="data.document" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

export default defineComponent({
  name: 'HomeView',
  components: {
    HelloWorld,
  },
  setup () {
    const data = ref(Object());
    const showVideo = ref(false);
    const showAudio = ref(false);
    const showDocument = ref(false)
    data.value = {
      image: "https://music.casio.com/assets/img/casiotone/pc/model/LK-S450FK-slide-1.jpg",
      video: "https://www.youtube.com/embed/0tIe_fyX9fw",
      document: "https://support.casio.com/en/manual/008/CTS400_quickstartguide_EN.pdf",
      audios: [
        "https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/998946304%3Fsecret_token%3Ds-Kd1t9sNrWRw&color=%23c7b26d&inverse=false&auto_play=false&show_user=true",
        "https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/998946346%3Fsecret_token%3Ds-UJ8QnIn0awm&color=%23c7b26d&inverse=false&auto_play=false&show_user=true",
        "https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/998946316%3Fsecret_token%3Ds-HtdgqB4S3D7&color=%23c7b26d&inverse=false&auto_play=false&show_user=true"
      ]
    }
    const showInfo = function(type: String) {
      if(type === 'video'){
        showVideo.value = true;
        showAudio.value = false;
        showDocument.value = false;
      }
      else if(type === 'audio') {
        showAudio.value = true;
        showVideo.value = false;
        showDocument.value = false;
      }
      else if(type === 'document') {
        showDocument.value = true;
        showAudio.value = false;
        showVideo.value = false;
      }
    }

    return {
      data,
      showVideo,
      showAudio,
      showDocument,
      showInfo
    }
  }
});
</script>
<style>
.keyboard-dim {
  max-width: 350px;
  transition: 0.3s;
}
.keyboard-dim:hover {
  max-width: 380px;
  box-shadow: 0 1em 1em #766969;
}
</style>
