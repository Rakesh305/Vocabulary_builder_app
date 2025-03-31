<template>
  <div class="container">
    <div class="card">
      <button @click="refreshWords" class="refresh-button">Refresh</button>
      <h2>Vocabulary Words</h2>
      <div v-for="(word, index) in words" :key="index" class="word-container">
        <div @click="toggleMeaning(index)" class="word">
          {{ word.term }}
        </div>
        <p v-if="word.showMeaning" class="meaning">{{ word.meaning }}</p>
      </div>
    </div>
  </div>
</template>

<script>
const wordBank = [
  { term: 'Ephemeral', meaning: 'Lasting for a very short time.' },
  {
    term: 'Obfuscate',
    meaning: 'To render obscure, unclear, or unintelligible.',
  },
  {
    term: 'Quixotic',
    meaning: 'Exceedingly idealistic; unrealistic and impractical.',
  },
  { term: 'Ubiquitous', meaning: 'Present, appearing, or found everywhere.' },
  { term: 'Ebullient', meaning: 'Cheerful and full of energy.' },
  { term: 'Cacophony', meaning: 'A harsh, discordant mixture of sounds.' },
  {
    term: 'Pernicious',
    meaning: 'Having a harmful effect, especially in a gradual way.',
  },
  {
    term: 'Sycophant',
    meaning:
      'A person who acts obsequiously toward someone important to gain advantage.',
  },
  {
    term: 'Intransigent',
    meaning: 'Unwilling or refusing to change one’s views.',
  },
  { term: 'Loquacious', meaning: 'Tending to talk a great deal; talkative.' },
  {
    term: 'Superfluous',
    meaning: 'Unnecessary, especially through being more than enough.',
  },
  {
    term: 'Ineffable',
    meaning: 'Too great or extreme to be expressed in words.',
  },
  { term: 'Auspicious', meaning: 'Conducive to success; favorable.' },
  {
    term: 'Serendipity',
    meaning: 'The occurrence of events by chance in a happy or beneficial way.',
  },
  {
    term: 'Luminous',
    meaning: 'Full of or shedding light; bright or shining.',
  },
];

export default {
  data() {
    return {
      words: [],
    };
  },
  created() {
    this.refreshWords();
  },
  methods: {
    toggleMeaning(index) {
      this.words[index].showMeaning = !this.words[index].showMeaning;
    },
    refreshWords() {
      this.words = wordBank
        .sort(() => 0.5 - Math.random())
        .slice(0, 10)
        .map((word) => ({ ...word, showMeaning: false }));
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(to right, #212529, #fa5252);
  <!-- background: #212529; -->
  padding: 20px;
}

.card {
  background: white;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
  text-align: center;
  max-width: 400px;
  width: 100%;
}

.refresh-button {
  background: #40c057;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 15px;
  transition: background 0.3s;
}

.refresh-button:hover {
  background: #218838;
}

h2 {
  margin-bottom: 20px;
  font-size: 24px;
  color: #333;
}

.word-container {
  margin-bottom: 15px;
}

.word {
  padding: 12px;
  border-radius: 8px;
  background: #228be6;
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}

.word:hover {
  background: #0056b3;
  transform: scale(1.05);
}

.meaning {
  margin-top: 10px;
  padding: 10px;
  background: #ced4da;
  border-radius: 8px;
  color: #333;
  font-size: 16px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}
</style>
