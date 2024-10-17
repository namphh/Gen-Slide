<template>
  <div class="about">
    <div v-html="renderedSlide" :class="['slide', 'slide-' + currentSlide]"></div>
    <div class="slide-counter">
      Slide {{ currentSlide + 1 }} of {{ slides.length }}
    </div>
    <div class="navigation">
      <button @click="prevSlide" :disabled="currentSlide === 0">Previous</button>
      <button @click="nextSlide" :disabled="currentSlide === slides.length - 1">Next</button>
    </div>
  </div>
</template>

<script>
import { marked } from 'marked';
import hljs from 'highlight.js'; // Import highlight.js library
import 'highlight.js/styles/github.css'; // Style for highlight.js

export default {
  data() {
    return {
      slides: [],
      currentSlide: 0,
      markdownContent: `---\n# Hướng Dẫn Sử Dụng Markdown\n\nMarkdown là một ngôn ngữ đánh dấu nhẹ, cho phép bạn định dạng văn bản một cách dễ dàng.\n\n## Nội Dung\n\n1. **Giới thiệu**\n2. **Cú pháp cơ bản**\n3. **Ví dụ**\n\n## 1. Giới thiệu\n\nMarkdown được sử dụng rộng rãi trong viết tài liệu, tạo README, và nhiều ứng dụng khác nhờ vào sự đơn giản và dễ đọc.\n\n## 2. Cú pháp cơ bản\n\n### Tiêu đề\n\nBạn có thể tạo các tiêu đề với số lượng dấu \`#\`:\n\n# Tiêu đề 1\n## Tiêu đề 2\n### Tiêu đề 3\n\n### Định dạng văn bản\n\n- **In đậm**: \`**văn bản**\` hoặc \`__văn bản__\`\n- *In nghiêng*: \`*văn bản*\` hoặc \`_văn bản_\`\n- ~~Gạch ngang~~: \`~~văn bản~~\`\n\n### Danh sách\n\n#### Danh sách không thứ tự\n\n- Mục 1\n- Mục 2\n  - Mục con 1\n  - Mục con 2\n\n#### Danh sách có thứ tự\n\n1. Mục 1\n2. Mục 2\n   1. Mục con 1\n   2. Mục con 2\n\n### Bảng\n\n| Cột 1   | Cột 2   | Cột 3   |\n|---------|---------|---------|\n| Dữ liệu 1 | Dữ liệu 2 | Dữ liệu 3 |\n| Dữ liệu 4 | Dữ liệu 5 | Dữ liệu 6 |\n\n### Khối mã\n\nBạn có thể chèn mã nguồn bằng cách sử dụng dấu \` \` \` cho đoạn mã đơn:\n\n\`console.log('Hello, World!');\`\n\nHoặc sử dụng ba dấu \` \` \` cho khối mã:\n\n\`\`\`javascript\nfunction greet() {\n    console.log("Hello, World!");\n}\ngreet();\n\`\`\`\n---`, // Ensure there is a delimiter at the start and end
    };
  },
  computed: {
    renderedSlide() {
      // Render markdown to HTML and highlight embedded code
      return marked(this.slides[this.currentSlide], {
        highlight: (code, lang) => {
          const validLang = hljs.getLanguage(lang) ? lang : 'plaintext';
          return hljs.highlight(validLang, code).value;
        },
      });
    },
  },
  methods: {
    nextSlide() {
      if (this.currentSlide < this.slides.length - 1) {
        this.currentSlide++;
      }
    },
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--;
      }
    },
    handleKeydown(event) {
      if (event.code === 'Space') {
        event.preventDefault(); // Prevent page scroll
        this.nextSlide();
      }
    },
    splitSlides(content) {
      // Split content into slides using the delimiter '---'
      return content.trim().split(/^\s*---\s*$/gm).filter(Boolean); // Remove empty elements
    },
  },
  created() {
    this.slides = this.splitSlides(this.markdownContent);
    window.addEventListener('keydown', this.handleKeydown); // Listen for keydown events
  },
  beforeDestroy() {
    window.removeEventListener('keydown', this.handleKeydown); // Cleanup listener when component is destroyed
  },
};
</script>

<style>
.about {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.slide {
  padding: 20px;
  font-size: 24px;
  border: 1px solid #ccc;
  margin: 20px 0;
  transition: opacity 0.5s;
}

.navigation {
  position: fixed;
  bottom: 20px; /* Space from the bottom */
  display: flex;
  gap: 10px;
  justify-content: center;
  width: 100%;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

/* Add transition effects between slides */
.slide-enter-active, .slide-leave-active {
  transition: opacity 0.5s;
}

.slide-enter, .slide-leave-to {
  opacity: 0;
}

/* Counter for slide number */
.slide-counter {
  font-size: 18px;
  margin-bottom: 10px;
}
</style>
