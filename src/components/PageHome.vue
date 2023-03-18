<template>
  <div class="container">
    <div class="col-large push-top">
      <!-- <ul class="breadcrumbs">
        <li>
          <a href="#"><i class="fa fa-home fa-btn"></i>Home</a>
        </li>
        <li><a href="category.html">Discussions</a></li>
        <li class="active"><a href="#">Cooking</a></li>
      </ul> -->
      <div class="post-list">
        <div class="post" v-for="post in posts" :key="post.id">
          <div class="user-info">
            <a href="profile.html#profile-details" class="user-name">{{
              userById(postById(post.id).userId).name
            }}</a>

            <a href="profile.html#profile-details">
              <img
                class="avatar-large"
                :src="userById(postById(post.id).userId).avatar"
                alt=""
              />
            </a>
            <!-- <p class="desktop-only text-small">107 posts</p>

            <p class="desktop-only text-small">23 threads</p>

            <span class="online desktop-only">online</span> -->
          </div>

          <div class="post-content">
            <div>
              <p>
                {{ postById(post.id).text }}
              </p>
            </div>
          </div>

          <!-- <div class="post-date text-faded">6 hours ago</div> -->

          <!-- <div class="reactions">
            <ul>
              <li>💡</li>
              <li>❤️</li>
              <li>👎</li>
              <li>👍</li>
              <li>👌</li>
            </ul>
            <button class="btn-xsmall"><span class="emoji">❤️</span>️ 3</button>
            <button class="btn-xsmall active-reaction">
              <span class="emoji">👌️</span>️ 1
            </button>
            <button class="btn-xsmall">
              + <i class="fa fa-smile-o emoji"></i>
            </button>
          </div> -->
        </div>
      </div>
    </div>
  </div>

  <!-- <div class="forum-stats desktop-only">
    <hr />
    <ul>
      <li><i class="fa fa-user-circle-o"></i>47 users online</li>
      <li><i class="fa fa-user-o"></i>497 users registered</li>
      <li><i class="fa fa-comments-o"></i>49 threads</li>
      <li><i class="fa fa-comment-o"></i>763 posts</li>
    </ul>
  </div> -->
</template>
<script setup>
import sourceData from '@/data.json'
import { ref } from 'vue'
const threads = ref(sourceData.threads)
const posts = ref(sourceData.posts)
const users = ref(sourceData.users)
function postById (postId) {
  return posts.value.find((p) => p.id === postId)
}
function userById (userId) {
  return users.value.find((p) => p.id === userId)
}
</script>
