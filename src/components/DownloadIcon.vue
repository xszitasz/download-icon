<template>
  <div @click="download" class="download-div">
    <!-- PDF type -->
    <div
      v-if="!downloading && fileType === 'pdf'"
      class="symbols">
      <i
        class="far fa-file-pdf"
        style="font-size: 48px;"
      ></i>
    </div>

    <!-- TXT Type -->
    <div
      v-if="!downloading && fileType === 'txt'"
      class="symbols"
    >
      <i
        class="far fa-file"
        style="font-size: 48px;"
      ></i>
    </div>

    <!-- Loader Section -->
    <div v-if="downloading" class="loader"></div>
    <div>
      <p class="document-text">{{ docName }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'DownloadIcon',
  data() {
    return {
      downloading: false,
    };
  },
  props: {
    docName: String,
    file: String,
    fileType: String
  },
  methods: {
    async download() {
      try {
        this.downloading = true;

        // Fetch the content from the API
        const response = await axios.get(this.file, {
          responseType: this.fileType === 'pdf' ? 'arraybuffer' : 'text',
        });

        const contentType = this.fileType === 'pdf' ? 'application/pdf' : 'text/plain';

        // Create a Blob containing the content
        const blob = new Blob([response.data], { type: contentType });

        // Create a download link
        const link = document.createElement('a');
        link.href = window.URL.createObjectURL(blob);
        link.download = `${this.fileType}` + '_file.' + `${this.fileType}`;
        link.click();

        this.downloading = false;
      } catch (error) {
        console.error('Error:', error);
        this.downloading = false;
      }
    }
  }
};
</script>

<style scoped>
@import '~@fortawesome/fontawesome-free/css/all.css';

.document-text {
  text-align: left;
  vertical-align: middle;
}

.download-div {
  cursor: pointer;
  display: flex;
  flex-wrap: nowrap;
  align-items: center;
  padding: 10px;
  margin: 1rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.symbols {
  border: 6px solid transparent;
  margin: 0.5rem;
  width: 40px;
  height: 40px;
}

.fa {
  cursor: pointer;
  margin: 0.5rem;
}

.loader {
  border: 6px solid #f3f3f3;
  border-top: 6px solid #2c3e50;
  border-radius: 50%;
  margin: 0.5rem;
  width: 40px;
  height: 40px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

@media (max-width: 320px) {
  .document-text {
    text-align: center;
  }
}

@media (max-width: 500px) {
  .document-text {
    text-align: center;
    vertical-align: middle;
    margin-left: 0;
  }
}
</style>