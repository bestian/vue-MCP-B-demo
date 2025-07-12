<template>
  <div class="about">
    <div class="about-content">
      <h1>About This Demo</h1>
      <p>
        This demo showcases how to embed MCP-B in a Vue3 project. Through this project, you can learn how to use the MCP-B framework to build modern web applications and experience its powerful tool integration capabilities and intelligent agent system.
      </p>
      <h1>About MCP-B</h1>

      <section class="intro">
        <h2>What is MCP-B?</h2>
        <p>
          MCP-B is an innovative AI agent framework based on the Model Context Protocol (MCP), designed for building intelligent and scalable AI applications.
          It provides powerful tool integration capabilities, enabling developers to easily create AI agents with rich functionality.
        </p>
      </section>

      <section class="features">
        <h2>Key Features</h2>
        <ul>
          <li><strong>Tool Integration</strong>: Seamless integration with various tools and APIs</li>
          <li><strong>Scalability</strong>: Modular architecture for easy extension and customization</li>
          <li><strong>Intelligent Agents</strong>: Smart agent system based on the MCP protocol</li>
          <li><strong>Developer Friendly</strong>: Complete development tools and documentation</li>
        </ul>
      </section>

      <section class="resources">
        <h2>Official Resources</h2>
        <p>
          Learn more about MCP-B and view detailed information by visiting the official documentation:
        </p>
        <a
          href="https://mcp-b.ai/blogs?showTodos=false&sortBy=created_at&sortOrder=desc"
          target="_blank"
          rel="noopener noreferrer"
          class="official-link"
        >
          MCP-B Official Documentation
        </a>
      </section>

      <section class="demo-info">
        <h2>About This Demo Project</h2>
        <p>
          This is a Vue.js-based MCP-B demonstration project that showcases how to build modern web applications using the MCP-B framework.
        </p>
      </section>
    </div>
  </div>
</template>

<style scoped>
.about {
  padding: 2rem;
  max-width: 800px;
  margin: 0 auto;
}

.about-content {
  line-height: 1.6;
}

h1 {
  color: #2c3e50;
  margin-bottom: 2rem;
  text-align: center;
}

h2 {
  color: #34495e;
  margin-top: 2rem;
  margin-bottom: 1rem;
  border-bottom: 2px solid #3498db;
  padding-bottom: 0.5rem;
}

section {
  margin-bottom: 2rem;
}

ul {
  list-style-type: none;
  padding-left: 0;
}

li {
  margin-bottom: 0.5rem;
  padding-left: 1.5rem;
  position: relative;
}

li::before {
  content: "•";
  color: #3498db;
  font-weight: bold;
  position: absolute;
  left: 0;
}

.official-link {
  display: inline-block;
  background-color: #3498db;
  color: white;
  padding: 0.75rem 1.5rem;
  text-decoration: none;
  border-radius: 5px;
  margin-top: 1rem;
  transition: background-color 0.3s ease;
}

.official-link:hover {
  background-color: #2980b9;
}

.demo-info {
  background-color: #f8f9fa;
  padding: 1.5rem;
  border-radius: 8px;
  border-left: 4px solid #3498db;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
