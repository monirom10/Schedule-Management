<template>
  <div class="container">
    <!-- @side-bar -->
    <div v-if="isSidebarOpen" class="container-sidebar" :class="{ 'closed': !isSidebarOpen }">  
        <ul class="sidebar-content">
          <li v-for="(item, index) in sidebarItems" :key="index">
            <span class="content-title" @click="handleClick(index)" :class="{ active: activeIndex === index }">
              <i :class="item.icon"></i>
              {{ item.title }}
              <i class="fa fa-chevron-down"></i>
            </span>

            <ul class="list inner" :class="{ slow: activeIndex === index }" v-if="activeIndex === index">
              <div class="content">
                <li v-for="(subItem, subIndex) in item.subItems" :key="subIndex" class="sub-item">
                  {{ subItem }}
                </li>
              </div>
            </ul>
          </li>
        </ul>
    </div>
    
    <!-- @tabe-calendar -->
    <div class="container-main" :class="{ 'sidebar-closed': !isSidebarOpen }" :style="{ width: isSidebarOpen ? 'calc(100% - 250px)' : '100%' }">
      <div class="hr">
        <hr>
      </div>
      <div class="custom-header-title">
        Schedule Management
      </div>
      <!-- @button-week -->
        <div v-for="weekNumber in 16" :key="weekNumber" class="select-week">
          <form action="">
            <select name="week">
              <option :value="week1">Week1</option>
              <option :value="week2">Week2</option>
              <option :value="week3">Week3</option>
              <option :value="week4">Week4</option>
              <option :value="week5">Week5</option>
              <option :value="week6">Week6</option>
              <option :value="week7">Week7</option>
              <option :value="week8">Week8</option>
              <option :value="week9">Week9</option>
              <option :value="week10">Week10</option>
              <option :value="week11">Week11</option>
              <option :value="wee12">Week12</option>
              <option :value="week13">Week13</option>
              <option :value="week14">Week14</option>
              <option :value="week15">Week15</option>
              <option :value="week16">Week16</option>
            </select> 
          </form>
        </div>  
      <div class="fullcalendar">
        <FullCalendar :options="calendarOptions">

        </FullCalendar> 
      </div>
      <div class="other-element" :class="{ 'expanded': isSidebarOpen }">
        <!-- <h2>Schedule Management</h2> -->
      </div>
    </div>
    <!-- @Drag N Drop -->
    <div class="drag-drop">
      <!-- @search-subject -->
      <div class="subject">
        <div class="search-subject">
          <form action="">
            <input type="text" placeholder="Search Subject">
            <button>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
              </svg>
            </button>
          </form>
        </div>
        <div class="select-subject">
          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>

          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>

          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>

          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>

          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>

          <div class="subject-box">
            <h1>Food Chemistry II</h1>
            <p>Unsigned</p>
            <span>TP : 32 H</span>
          </div>
        </div>
      </div>
      
      <!-- @search-room -->
      <div class="room-lecturer">
        <div class="tabs">
          <button @click="changeTab('room')" :class="{ active: currentTab === 'room' }">Room</button>
          <button @click="changeTab('lecturer')" :class="{ active: currentTab === 'lecturer' }">Lecturer</button>
        </div>

        <div class="search-subject">
          <form action="">
            <input type="text" placeholder="Search Subject">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
            </svg>
          </form>
        </div>

        <div class="room-lecturer-content">
          <div class="room-tab" v-if="currentTab === 'room'">
            <div class="room-box">
              <!-- @room-number -->
              <div class="room-number">
                  <h1>106 F</h1>
              </div>
              <!-- @room-name -->
              <div class="room-name">
                  <h2>Learning Room</h2>
                  <p>N/A Desk</p>
                  <p>N/A Chair</p>
              </div>
          </div>

          <div class="room-box">
              <!-- @room-number -->
              <div class="room-number">
                  <h1>101 A</h1>
              </div>
              <!-- @room-name -->
              <div class="room-name">
                  <h2>Conference Room</h2>
                  <p>N/A Desk</p>
                  <p>N/A Chair</p>
              </div>
          </div>

          <div class="room-box">
              <!-- @room-number -->
              <div class="room-number">
                  <h1>101 A</h1>
              </div>
              <!-- @room-name -->
              <div class="room-name">
                  <h2>Conference Room</h2>
                  <p>N/A Desk</p>
                  <p>N/A Chair</p>
              </div>
          </div>

          <div class="room-box">
              <!-- @room-number -->
              <div class="room-number">
                  <h1>101 A</h1>
              </div>
              <!-- @room-name -->
              <div class="room-name">
                  <h2>Conference Room</h2>
                  <p>N/A Desk</p>
                  <p>N/A Chair</p>
              </div>
          </div>

          <div class="room-box">
              <!-- @room-number -->
              <div class="room-number">
                  <h1>101 A</h1>
              </div>
              <!-- @room-name -->
              <div class="room-name">
                  <h2>Conference Room</h2>
                  <p>N/A Desk</p>
                  <p>N/A Chair</p>
              </div>
          </div>
        </div>

        <div class="lecturer-tab" v-if="currentTab === 'lecturer'">
          <div class="lecturer-box">
            <!-- @lecturer-profile -->
            <div class="lecturer-profile">
              <img src="../assets/Logo/avatar.png" alt="">
            </div>
            <!-- @lecturer-info -->
            <div class="lecturer-info">
              <h3>No ID Card | Iron Man</h3>
              <p>Iron Man</p>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.332A48.36 48.36 0 0012 9.75c-2.551 0-5.056.2-7.5.582V21M3 21h18M12 6.75h.008v.008H12V6.75z" />
              </svg>
              <span>TC | Gender: Male</span>
            </div>
          </div>

          <div class="lecturer-box">
            <!-- @lecturer-profile -->
            <div class="lecturer-profile">
              <img src="../assets/Logo/avatar.png" alt="">
            </div>
            <!-- @lecturer-info -->
            <div class="lecturer-info">
              <h3>No ID Card | Iron Man</h3>
              <p>Iron Man</p>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.332A48.36 48.36 0 0012 9.75c-2.551 0-5.056.2-7.5.582V21M3 21h18M12 6.75h.008v.008H12V6.75z" />
              </svg>
              <span>TC | Gender: Male</span>
            </div>
          </div>

          <div class="lecturer-box">
            <!-- @lecturer-profile -->
            <div class="lecturer-profile">
              <img src="../assets/Logo/avatar.png" alt="">
            </div>
            <!-- @lecturer-info -->
            <div class="lecturer-info">
              <h3>No ID Card | Iron Man</h3>
              <p>Iron Man</p>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.332A48.36 48.36 0 0012 9.75c-2.551 0-5.056.2-7.5.582V21M3 21h18M12 6.75h.008v.008H12V6.75z" />
              </svg>
              <span>TC | Gender: Male</span>
            </div>
          </div>

          <div class="lecturer-box">
            <!-- @lecturer-profile -->
            <div class="lecturer-profile">
              <img src="../assets/Logo/avatar.png" alt="">
            </div>
            <!-- @lecturer-info -->
            <div class="lecturer-info">
              <h3>No ID Card | Iron Man</h3>
              <p>Iron Man</p>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.332A48.36 48.36 0 0012 9.75c-2.551 0-5.056.2-7.5.582V21M3 21h18M12 6.75h.008v.008H12V6.75z" />
              </svg>
              <span>TC | Gender: Male</span>
            </div>
          </div>

          <div class="lecturer-box">
            <!-- @lecturer-profile -->
            <div class="lecturer-profile">
              <img src="../assets/Logo/avatar.png" alt="">
            </div>
            <!-- @lecturer-info -->
            <div class="lecturer-info">
              <h3>No ID Card | Iron Man</h3>
              <p>Iron Man</p>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.332A48.36 48.36 0 0012 9.75c-2.551 0-5.056.2-7.5.582V21M3 21h18M12 6.75h.008v.008H12V6.75z" />
              </svg>
              <span>TC | Gender: Male</span>
            </div>
          </div>
        </div>
        </div>
      </div>

    </div>

     <!-- Button to toggle the side-bar -->
    <button class="toggle-button" @click="toggleSidebar">
      <h1>X</h1>
    </button>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import FullCalendar from '@fullcalendar/vue3'
import timeGridPlugin from '@fullcalendar/timegrid'
import interactionPlugin from '@fullcalendar/interaction'
import { INITIAL_EVENTS, createEventId } from '../event-utils'
// import { LoginIcon } from "@vue-hero-icons/outline"
// import { IconifyIcon } from '@iconify/vue';

export default defineComponent({
  name: 'CustomHeaderTitle',
  components: {
    FullCalendar,
  },
  data() {
    return {
      currentTab: 'room', // Initial active tab
      sidebarItems: [
        {
          title: 'Acedemy Year',
          icon: 'fa fa-home',
          subItems: [
            '2022 - 2023', 
            '2023 - 2024', 
            '2025 - 2025'
          ]
        },
        {
          title: 'Department',
          icon: 'fa fa-cog',
          subItems: [
            'GIC',
            'GCA',
            'GTR'
          ]
        },
        {
          title: 'Levels',
          icon: 'fa fa-envelope',
          subItems: [
            'Engeener',
            'Degree',
            'Master'
          ]
        },
        {
          title: 'Options',
          icon: 'fa fa-users',
          subItems: [
            'Food Technology',
            'Crush Technology',
            'Sl-Ke Alone Technology'
          ]
        },
        {
          title: 'Years',
          icon: 'fa fa-users',
          subItems: [
            'Year one',
            'Year two',
            'Year three',
            'Year Four',
            'Year Five'
          ]
        },
        {
          title: 'Semesters',
          icon: 'fa fa-users',
          subItems: [
            'Semester I',
            'Semester II'
          ]
        },
        {
          title: 'Groups',
          icon: 'fa fa-users',
          subItems: [
            'A',
            'B',
            'C'
          ]
        }
      ],
      isDraggingBox: false, // Flag to track box dragging
      activeIndex: null,
      calendarOptions: {
        plugins: [
          timeGridPlugin,
          interactionPlugin // needed for dateClick
        ],
        headerToolbar: {
          right: 'timeGridWeek'
        },
        initialView: 'timeGridWeek', // Set the initial view to week
        initialEvents: INITIAL_EVENTS,
        editable: true,
        selectable: true,
        selectMirror: true,
        weekends: true,
        select: this.handleDateSelect,
        eventClick: this.handleEventClick,
        eventsSet: this.handleEvents,
        // Hide the Sunday column
        hiddenDays: [0], // 0 corresponds to Sunday
        // Adjust the visible hours
        slotMinTime: '07:00:00 ', // Set the minimum time to 7 AM
        slotMaxTime: '18:00:00 ', // Set the maximum time to 5 PM
        // Change the time format to display minutes
        slotLabelFormat: {
          hour: 'numeric',
          minute: '2-digit',
          omitZeroMinute: false,
          meridiem: 'short'
        },
        // Remove the row of all-day slot names
        allDaySlot: false,
        
        views:{
          timeGridWeek: {
            dayHeaderContent: this.customDayHeaderContent
          },
          
        },
        // Update the headerToolbar configuration
        headerToolbar: {
          start: '', // will normally be on the left. if RTL, will be on the right
          center: '',
          end: 'timeGridWeek' // will normally be on the right. if RTL, will be on the left
        }
      },
      currentEvents: [],
      isSidebarOpen: true,// Initial state of the side-bar
    }
  },
  methods: {
    changeTab(tabName) {
      this.currentTab = tabName;
    },
    // Custom function to format day header labels
    customDayHeaderContent(args) {
      const date = new Date(args.date);
      const day = date.toLocaleDateString('en-US', { weekday: 'long' }); // Change 'long' to 'short' if you prefer abbreviated names
      return day;
    },
    toggleSidebar() {
      this.isSidebarOpen = !this.isSidebarOpen;
    },
    handleWeekendsToggle() {
      this.calendarOptions.weekends = !this.calendarOptions.weekends // update a property
    },
    handleDateSelect(selectInfo) {
      let title = prompt('Please enter a new title for your event')
      let calendarApi = selectInfo.view.calendar

      calendarApi.unselect() // clear date selection

      if (title) {
        calendarApi.addEvent({
          id: createEventId(),
          title,
          start: selectInfo.startStr,
          end: selectInfo.endStr,
          allDay: selectInfo.allDay
        })
      }
    },
    handleEventClick(clickInfo) {
      if (confirm(`Are you sure you want to delete the event '${clickInfo.event.title}'`)) {
        clickInfo.event.remove()
      }
    },
    handleEvents(events) {
      this.currentEvents = events
    },
    handleClick(index) {
      if (this.activeIndex === index) {
        this.activeIndex = null;
      } else {
        this.activeIndex = index;
      }
    }
    
  },
  
})
</script>
