<template>
  <main class="container">
    <h3><span>Upload</span> Files</h3>
    <div class="main-content">
      <div class="dropzone">
        <div class="dropzone-text">
          <h4>Drop your files here.</h4>
          <span>or</span>
          <label for="files" class="upload-btn">Browse</label>
        </div>
        <input
          type="file"
          multiple
          id="files"
          @change="uploadFiles($event)"
          accept="image/png, image/gif, image/jpeg, video/*"
        />
      </div>
      <div class="output-container">
        <ul class="files-list" v-if="files.length > 0">
          <li class="file-detail" v-for="(file, index) in files" :key="index">
            <img
              :src="file.url"
              alt="thumbnail"
              class="thumbnail"
              v-if="file.type.startsWith('image')"
            />
            <div v-if="file.type.startsWith('video')">
              <video id="video-element" currentTime="2" allowfulscreen>
                <source :src="file.url" type="video/mp4" />
              </video>
            </div>
            <div class="file-info">
              <p><span>Name:</span> {{ file.name }}</p>
              <p><span>Type:</span> {{ file.type }}</p>
              <p><span>Size:</span> {{ file.size }}</p>
            </div>
            <div>
              <button class="remove-btn" @click="removeFile(index)">
                <img src="../assets/delete.png" alt="" />
              </button>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MediaPicker",

  data() {
    return {
      files: [],
    };
  },

  methods: {
    uploadFiles(e) {
      const files = Array.from(e.target.files);
      this.files.push(
        ...files.map((file) => {
          return {
            name: file.name,
            type: file.type,
            size: file.size / 1000,
            url: URL.createObjectURL(file),
          };
        })
      );
    },

    removeFile(index) {
      this.files.splice(index, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  min-width: 800px;
  height: 550px;
  width: 1000px;
  background-color: #fff;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  border-radius: 1rem;
  overflow: hidden;
  padding: 2rem;
}

h3 {
  text-transform: uppercase;
  letter-spacing: 1px;
  margin-bottom: 2rem;
  font-weight: 500;
}

h3 span {
  color: #0b6adc;
}

.main-content {
  display: flex;
  height: 100%;
  padding-bottom: 3.5rem;
}

.dropzone,
.output-container {
  height: 100%;
  flex: 1;
}

.dropzone {
  position: relative;
  margin-right: 4rem;
}

.dropzone::after {
  content: "";
  background: url("../assets/dropzone2.jpg");
  background-size: cover;
  background-position: bottom center;
  opacity: 0.4;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: 1;
  border-radius: 1.5rem;
  border: 2px dashed #0b6adc;
}

.dropzone-text {
  text-align: center;
  z-index: 10;
  position: absolute;
  left: 50%;
  bottom: 10%;
  transform: translateX(-50%);
}

.dropzone-text h4 {
  font-weight: 300;
  font-size: 1.5rem;
  letter-spacing: 1px;
  white-space: nowrap;
  color: rgb(94, 94, 94);
}

.dropzone-text span {
  margin-right: 0.5rem;
  font-size: 1.2rem;
  color: rgb(100, 99, 99);
}

.upload-btn {
  color: #0b6adc;
  font-weight: bold;
  font-size: 1rem;
  cursor: pointer;
}

#files {
  display: none;
}

.output-container {
  overflow-y: scroll;
  padding-right: 1rem;
}

.output-container::-webkit-scrollbar {
  width: 10px; /* width of the entire scrollbar */
}
.output-container::-webkit-scrollbar-track {
  background: rgb(224, 224, 224); /* color of the tracking area */
}
.output-container::-webkit-scrollbar-thumb {
  background-color: rgba(11, 106, 220, 0.5);
  border-radius: 20px;
}

.output-container .file-detail {
  background-color: #fff;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  padding: 1rem;
  border-radius: 0.7rem;
  transition: all 0.5s ease;
  transform: translate(0rem, 0rem);
}

.output-container .file-detail:hover {
  transform: translate(-0.5rem, 0.5rem);
}

.output-container .files-list {
  list-style: none;
}

.output-container .file-detail {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1.5rem;
}
.output-container .thumbnail {
  height: 100px;
  width: 100px;
  border-radius: 0.5rem;
  object-fit: cover;
}

#video-element {
  width: 100px;
  height: 100px;
}

.output-container .file-info {
  flex: 1;
  margin-left: 1.5rem;
}

.file-info p {
  margin-bottom: 0.2rem;
}

.file-detail p span {
  font-weight: bold;
}

.output-container .remove-btn {
  background-color: transparent;
  border: none;
  cursor: pointer;
}
.output-container .remove-btn img {
  height: 30px;
  width: 30px;
}
</style>
