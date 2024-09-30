<template>
  <Dashboard>
    <Navbar :links="links" />
    
    <Sidebar>
      <!--
      <Link></Link>
        <Link></Link>
        <Link></Link>
        <Link></Link>
      <Link></Link>
      <Link></Link> -->
    </Sidebar>
    <Content>
      <!--
      <Stats>
        <Stat></Stat>
        <Stat></Stat>
        <Stat></Stat>
      </Stats>
      
      <Charts>
        <Chart></Chart>
        <Chart></Chart>
        <Chart></Chart>
      </Charts>
      <Table></Table>
      <List>
        <Item></Item>
        <Item></Item>
        <Item></Item>
        <Item></Item>
        <Item></Item>
      </List>-->
    </Content>
  </Dashboard>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
import Dashboard from './components/Dashboard.vue'
import Content from './components/Content.vue';
import Sidebar from './components/Sidebar.vue';

const links = [
  {
    label: 'test',
    href: 'test.com',
  },
  {
    label: 'test2',
    href: 'test.com',
  },
  {
    label: 'test3',
    href: 'test3.com',
    img: 'path/img',
    type: 'action',
  },
  {
    label: 'test4',
    img: 'path/img',
    type: 'action',
    dropdown: [
      {
        label: 'profile',
        href: 'profile'
      },
      {
        label: 'profile',
        href: 'profile'
      },
      {
        label: 'profile',
        href: 'profile'
      },
      {
        label: 'profile',
        href: 'profile',
        img: 'path/img'
      }
    ]
  },
  {
    label: 'test brand',
    img: 'path/to/img',
    alt: 'alt text',
    href: "test.com",
    type: 'brand'
  }
]
</script>



<style scoped>
</style>
