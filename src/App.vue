<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'

import { RouterLink, RouterView, useRouter } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

import { TabServerTransport } from '@mcp-b/transports';
import { McpServer } from '@modelcontextprotocol/sdk/server/mcp.js';
import { z } from 'zod';

export default defineComponent({
  name: 'DemoApp',
  components: {
    RouterLink,
    RouterView,
    HelloWorld
  },
  setup() {

    const count = ref(0)

    const addCount = (num: number) => {
      count.value += num
      return count.value
    }

    const router = useRouter()

    const gotoAbout = () => {
      router.push('/about')
    }


    onMounted(async () => {
      console.log('onMounted')


      const server = new McpServer({
        name: 'my-app',
        version: '1.0.0'
      });

      server.tool('sayHello', 'Says hello', {
        name: z.string()
      }, async ({ name }) => ({
        content: [{ type: 'text', text: `Hello ${name}!` }]
      }));


      await server.connect(new TabServerTransport({ allowedOrigins: ['*'] }));

      // This is a demo of how to call a Vue method on the server from the client
      server.tool('addCount', 'Adds a number to the count', {
        num: z.string()
      }, async ({ num }) => {
        addCount(Number(num))
        return {
          content: [{ type: 'text', text: `Added ${num} to the count!` }]
        }
      });

      server.tool('subtractCount', 'Subtracts a number from the count', {
        num: z.string()
      }, async ({ num }) => {
        addCount(-Number(num))
        return {
          content: [{ type: 'text', text: `Subtracted ${num} from the count!` }]
        }
      });

      // This is a demo of a tool that has no parameters and returns a string
      server.tool('getCount', 'Gets the current count', {}, async () => ({
        content: [{ type: 'text', text: `The current count is ${count.value}` }]
      }));

      // This is a demo of how to use the router in the MCP server
      server.tool('gotoAbout', 'Goes to the about page', {}, async () => {
        gotoAbout()
        return {
          content: [{ type: 'text', text: `Going to the about page!` }]
        }
      });
    })


    return {
      count,
      addCount,
      gotoAbout
    }
  }
})

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" :count="count" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
