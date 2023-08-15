<template>
    <div id="app">
      <div class="overlay" v-show="isClosed" @click="toggleSidebar"></div>
      <nav class="navbar navbar-inverse fixed-top" id="sidebar-wrapper" role="navigation" :class="{ 'toggled': !isClosed }">
        <ul class="nav sidebar-nav">
          <div class="sidebar-header">
            <div class="sidebar-brand">
              <a href="#">Brand</a>
            </div>
          </div>
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#events">Events</a></li>
          <li><a href="#team">Team</a></li>
          <li class="dropdown">
            <a href="#works" class="dropdown-toggle" @click.prevent="toggleDropdown">Works <span class="caret"></span></a>
            <ul class="dropdown-menu animated fadeInLeft" role="menu">
              <div class="dropdown-header">Dropdown heading</div>
              <li><a href="#pictures">Pictures</a></li>
              <li><a href="#videos">Videeos</a></li>
              <li><a href="#books">Books</a></li>
              <li><a href="#art">Art</a></li>
              <li><a href="#awards">Awards</a></li>
            </ul>
          </li>
          <li><a href="#services">Services</a></li>
          <li><a href="#contact">Contact</a></li>
          <li><a href="#followme">Follow me</a></li>
        </ul>
      </nav>
      <div id="page-content-wrapper" :class="{ 'toggled': !isClosed }">
        <button type="button" class="hamburger animated fadeInLeft is-closed" @click="toggleSidebar">
          <span class="hamb-top"></span>
          <span class="hamb-middle"></span>
          <span class="hamb-bottom"></span>
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isClosed: false,
      };
    },
    methods: {
      toggleSidebar() {
        this.isClosed = !this.isClosed;
      },
      toggleDropdown(event) {
        event.preventDefault();
        event.target.parentElement.classList.toggle('open');
      },
    },
  };
  </script>
  
  <style>
  /* Your CSS styles here */
  </style>
  