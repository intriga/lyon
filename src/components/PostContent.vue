<template>
    <div class="bloglist singlepost">
        <p><img alt="" class="img-fluid" :src="model.post.image"></p>
        <h1>{{ model.post.title }}</h1>
        <div class="postmeta">
            <ul>
                <li><a href="#"><i class="icon_folder-alt"></i> Collections</a></li>
                <li><a href="#"><i class="icon_clock_alt"></i> {{ format_date(model.post.created_at) }}</a></li>
                <li><a href="#"><i class="icon_pencil-edit"></i> Admin</a></li>
                <li><a href="#"><i class="icon_comment_alt"></i> (14) Comments</a></li>
            </ul>
        </div>
        <!-- /post meta -->
        <div class="post-content">
            <div class="dropcaps">
                <p v-html="model.post.content"></p>
            </div>
        </div>
        <!-- /post -->
    </div>
</template>

<script>
import axios from 'axios'
import moment from 'moment'

export default {
  data() {
    return {
      capturedSlug: null,
      model: {
        post: {
          title: '',
          image: '',
          content: '',
          created_at: ''
        }
      }
    }
  },

  mounted() {
    this.getPost()
  },

  methods: {
    getPost() {
      const urlFull = window.location.href
      const urlParts = urlFull.split('/')

      const slug = urlParts[urlParts.length - 1]
      //console.log(slug);

      axios.get(`http://localhost/api/post/${slug}`).then((res) => {
        this.post = res.data
        console.log(this.post)

        this.model.post = {
          title: res.data.title,
          image: res.data.image,
          content: res.data.content,
          created_at: res.data.created_at
        }
      })
    },

    format_date(value) {
      if (value) {
        return moment(String(value)).format('DD/MM/YYYY')
      }
    }
  }
}
</script>