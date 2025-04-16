<template>
  <section id="experience-section">
    <h2>What I've Been Working On</h2>

    <a
      v-for="(item, index) in cards"
      :key="index"
      :href="item.link || undefined"
      class="card"
      :class="{ 'scrolling': index < 3 }"
      target="_blank"
      rel="noopener noreferrer"
    >
      <div class="img-scroll">
        <img :src="item.image" :alt="item.title" class="card-img" />
      </div>
      <h3>{{ item.title }}</h3>
      <p class="role">{{ item.role }}</p>
      <p>{{ item.description }}</p>
      <div class="tags">
        <span v-for="tag in item.tags" :key="tag">{{ tag }}</span>
      </div>
    </a>
  </section>
</template>

<script setup>
const cards = [
  {
    image: new URL('../assets/img/atlas.png', import.meta.url).href,
    title: 'ATLAS: Adversarial Threat Landscape for AI Systems',
    role: 'MITRE',
    description:
      'On the ATLAS team, I helped develop a new system architecture, including the public site built with Vue.js and GitLab Pages, and an internal editor tool backed by MongoDB to manage AI threat data and integrate smoothly with existing user workflows. I also led major parts of a full site redesign and rebuild using Vue3 to meet MITRE’s privacy and branding standards.',
    tags: [
      'Vue.js', 'Pinia', 'MongoDB', 'HTML', 'Pytest', 'Front-End Development',
      'Back-End Development', 'CI/CD', 'Gitlab Pages', 'JSON Schema',
      'Vuetify', 'State Management', 'User Interface Design'
    ],
    link: 'https://atlas.mitre.org'
  },
  {
    image: new URL('../assets/img/mappings-explorer.png', import.meta.url).href,
    title: 'Mappings Explorer',
    role: 'MITRE',
    description:
      'On Mappings Explorer, I rebuilt the site using Nuxt and Vue to support a semi-static architecture for use by external partners. This effort aimed to greatly improved maintainability and flexibility while maintaining a clean and modern frontend.',
    tags: [
      'Nuxt', 'Vue.js', 'Web Architecture', 'Front-End Development',
      'Full-Stack Development', 'JavaScript', 'Nuxt.js', 'Web Development'
    ],
    link: 'https://center-for-threat-informed-defense.github.io/mappings-explorer/'
  },
  {
    image: new URL('../assets/img/attack-flow.png', import.meta.url).href,
    title: "ATT&CK Flow Builder",
    role: 'MITRE',
    description: 'On the ATT&CK Flow Builder team, I enhanced the frontend with Vue and TypeScript, implementing usability improvements. I collaborated closely with stakeholders to refine the user experience for cybersecurity professionals.',
    tags: [
      'TypeScript', 'Vue.js', 'Canvas', 'CSS', 'D3.js',
      'Front-End Development', 'Full-Stack Development', 'HCI',
      'User Experience (UX)', 'User Interface Design'
    ],
    link: 'https://center-for-threat-informed-defense.github.io/attack-flow/builder/'
  },
  {
    image: new URL('../assets/img/mitre.png', import.meta.url).href,
    title: 'ChatGPT Prompt Engineering',
    role: 'MITRE',
    description:
'As part of the prompt engineering team, I integrated ChatGPT into over six MITRE tools to automate tasks such as transcript summarization, project strategy exploration, and statement-of-work generation. I delivered presentations and trainings to over 300 employees on one of these tools and received multiple awards for my contributions.',    tags: [
      'ChatGPT', 'Prompt Engineering', 'Automation', 'Chatbot Responses',
      'Large Language Models (LLM)', 'Shell Scripting',
      'Synthetic Data Generation', 'Web Scraping', 'Microsoft Azure', 'Selenium'
    ],
    link: 'https://www.mitre.org/news-insights/news-release/mitre-wins-cio100-award-enterprise-implementation-generative-ai'
  },
  {
    image: new URL('../assets/img/whiteboarding.avif', import.meta.url).href,
    title: 'Software Project Manager',
    role: 'UMass Amherst',
    description:
      'While managing a team of 10 students, I led the development of a production-ready web app for Ultimate Kronos Group. I facilitated agile ceremonies, managed sprint planning and retrospectives, and helped my team maintain strong technical and collaborative momentum.',
    tags: [
      'Agile', 'Team Leadership', 'Web App', 'Adaptive Management',
      'Agile Project Management', 'Jira', 'Leadership', 'PostgreSQL',
      'Software Design', 'Task Management', 'Trello'
    ],
    link: null
  },
  {
    image: new URL('../assets/img/wlcp.png', import.meta.url).href,
    title: 'Wearable Learning Cloud Platform',
    role: 'UMass Amherst',
    description:
      'While contributing to WLCP research, I implemented and tested features on a Kotlin-based mobile app to support K–12 STEM learning. I worked closely with academic advisors to improve classroom usability through new visual and interactive enhancements.',
    tags: ['Kotlin', 'STEM Education', 'Research'],
    link: 'http://wearablelearning.org/#'
  },
  {
    image: new URL('../assets/img/coding-minds.png', import.meta.url).href,
    title: 'Coding Instructor',
    role: 'Coding Minds Academy',
    description:
      'While teaching K–12 students at Coding Minds, I developed custom project-based Python and Java courses using Git and MakeCode. I also created curriculum with Pygame and supported web dev lessons, helping students build their first interactive websites.',
    tags: [
      'Python', 'Java', 'Pygame', 'Git', 'MakeCode',
      'C++', 'GitHub', 'Web Development'
    ],
    link: 'https://codingmind.com/'
  }
];


</script>

<style scoped>
#experience-section {
  padding: 6rem 2rem;
  max-width: 900px;
  margin: 0 auto;
}

#experience-section h2 {
  font-size: 2.5rem;
  text-align: center;
  color: var(--color-heading);
  margin-bottom: 3rem;
}

.card {
  display: block;
  background: white;
  border-radius: 1rem;
  padding: 2rem;
  margin-bottom: 2rem;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.15);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;
  text-decoration: none;
  color: inherit;
  cursor: pointer;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
}

.img-scroll {
  height: 160px;
  overflow: hidden;
  border-radius: 0.75rem;
  margin-bottom: 1rem;
  position: relative;
}

.card-img {
  width: 100%;
  height: auto;
  object-fit: cover;
  object-position: top;
}

.card.scrolling .card-img {
  animation: scrollImage 10s ease-in-out infinite alternate;
}

@keyframes scrollImage {
  0% {
    transform: translateY(0);
  }
  20% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-50%);
  }
}

.card h3 {
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
  color: var(--color-heading);
}

.role {
  font-size: 0.95rem;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.75);
  margin-bottom: 1rem;
}

.card p {
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text);
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 1rem;
}

.tags span {
  background: #1452e3;
  color: white;
  padding: 0.3rem 0.75rem;
  font-size: 0.85rem;
  border-radius: 999px;
  white-space: nowrap;
  user-select: none;
}
</style>
