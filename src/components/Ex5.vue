<template>
  <div class="container">
    <div class="form-section">
      <h2>Customize Profile</h2>

      <label>Name:</label><br/>
      <input id="name" v-model="name" placeholder="Your Name"/><br/><br/>

      <label>Job Title:</label><br/>
      <input id="job" v-model="job" placeholder="Web Developer"/><br/><br/>

      <label>Bio:</label><br/>
      <textarea id="bio" v-model="bio" rows="3" placeholder="A short bio..."></textarea><br/><br/>

      <label>Profile Image URL:</label><br/>
      <input id="imageUrl" v-model="imageUrl" placeholder="/assets/head1.jpg or https://..."/><br/><br/>

      <label>Theme Presets:</label><br/>
      <button type="button" class="theme-button" @click="cycleTheme">Cycle theme</button>
    </div>

    <div class="preview-section">
      <h2>Live Preview</h2>
      <div class="preview-card" :style="previewStyle">
        <img :src="imageUrl" class="preview-img" alt="profile"/>
        <h3>{{ name || 'Your Name' }}</h3>
        <h4>{{ job || 'Job Title' }}</h4>
        <p>{{ bio || 'Write something about yourself...' }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Ex5',
  data() {
    return {
      name: '',
      job: '',
      bio: '',
      imageUrl: '/assets/head1.jpg',
      themes: [
        { id: 'dark',  bg: '#333333', text: '#ffffff' },
        { id: 'light', bg: '#ffffff', text: '#000000' },
        { id: 'neon',  bg: '#39ff14', text: '#000000' }
      ],
      currentThemeIndex: 0
    }
  },
  computed: {
    currentTheme() {
      return this.themes[this.currentThemeIndex];
    },
    previewStyle() {
      return {
        backgroundColor: this.currentTheme.bg,
        color: this.currentTheme.text
      };
    }
  },
  methods: {
    cycleTheme() {
      this.currentThemeIndex = (this.currentThemeIndex + 1) % this.themes.length;
      console.log('Theme changed to', this.currentTheme.id, 'index', this.currentThemeIndex);
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  gap: 20px;
  padding: 20px;
  font-family: sans-serif;
}

.form-section,
.preview-section {
  width: 50%;
}

.preview-card {
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: all 0.25s ease;
}

.preview-img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
  margin-bottom: 10px;
}

.theme-button {
  margin: 5px;
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

</style>
