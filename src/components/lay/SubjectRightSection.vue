<template>
  <div class="right-section">

    <h2 class="main-title">
      1. Subject of these Test Guidelines
    </h2>

    <!-- Related Links -->
    <div class="related-links">
      <span class="label">Related links:</span>
      <a href="#">More than one species (GN3)</a>
      <a href="#">Different types or groups within a species or genus (GN4)</a>
      <a href="#">Family name (GN5)</a>
      <a href="#">Guidance for New Types and Species (GN6)</a>
    </div>

    <!-- Main Card -->
    <div class="content-card">

      <p>
        These Test Guidelines apply to all varieties of
        <i>Malpighia emarginata</i> DC. Continue Sentence
      </p>

      <p class="question">
        Should clarification be provided that any other species or hybrids not explicitly covered by these Test Guidelines should be treated according to the provisions of document TGP/12 "Guidance for New Types and Species"?
      </p>

      <!-- Radio -->
      <div class="radio-group">
        <label>
          <input type="radio" value="Yes" v-model="clarification" />
          Yes
        </label>
        <label>
          <input type="radio" value="No" v-model="clarification" />
          No
        </label>
      </div>

      <!-- Input sentence -->
      <p>
        Guidance on the use of Test Guidelines for
        <input class="inline-input" v-model="hybridText" />
        that are not explicitly covered by Test Guidelines is provided in document TGP/13 "Guidance for New Types and Species"
      </p>

      <!-- Add Paragraph Button -->
      <button class="add-btn">
        + Add Paragraph
      </button>

      <p class="question">
        Might it be necessary to add additional characteristics or additional states of expressions for ornamental, fruit, industrial, vegetable, agricultural or other varieties?
      </p>

      <!-- Radio -->
      <div class="radio-group">
        <label>
          <input type="radio" value="Yes" v-model="additionalAnswer" />
          Yes
        </label>
        <label>
          <input type="radio" value="No" v-model="additionalAnswer" />
          No
        </label>
      </div>

      <p>
        In the case of
        <input class="inline-input" v-model="additionalType" />
        , in particular, it may be necessary to use additional characteristics or additional states of expression to those included in the Table of Characteristics in order to examine Distinctness, Uniformity and Stability.
      </p>

    </div>

    <!-- Preview -->
    <div class="preview-card">
      <div class="preview-title">PREVIEW</div>
      <p>
        1.1 These Test Guidelines apply to all varieties of
        Argania spinosa (L.) Skeels. Continue Sentence
      </p>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const clarification = ref('Yes')
const hybridText = ref('interspec. hybrids')
const additionalAnswer = ref('Yes')
const additionalType = ref('agricultural')
</script>

<style scoped>
.right-section {
  padding: 30px 40px;
  flex: 1;
  background: #f6f7f6;
}

.main-title {
  font-size: 22px;
  font-weight: 600;
  color: #1f3b37;
  margin-bottom: 20px;
}

.related-links {
  margin-bottom: 20px;
  font-size: 14px;
}

.related-links a {
  margin-right: 15px;
  color: #1f7a5c;
  text-decoration: none;
}

.content-card {
  background: white;
  padding: 25px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  margin-bottom: 25px;
}

.question {
  margin-top: 20px;
}

.radio-group {
  margin: 10px 0 15px 0;
}

.radio-group label {
  margin-right: 20px;
}

.inline-input {
  padding: 6px 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin: 0 5px;
}

.add-btn {
  margin: 15px 0;
  padding: 6px 14px;
  border: 1px solid #1f7a5c;
  background: white;
  color: #1f7a5c;
  border-radius: 20px;
  cursor: pointer;
}

.preview-card {
  background: #ececec;
  padding: 20px;
  border-radius: 8px;
}

.preview-title {
  font-weight: 600;
  margin-bottom: 10px;
}
</style>
