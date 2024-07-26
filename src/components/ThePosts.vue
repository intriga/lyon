<template>
    <div class="col-lg-9">
        <article class="blog "
                v-for="value in posts.data" :key="value">
            <div class="row g-0">
                <div class="col-lg-7">
                    <figure>
                        <a :href="value.slug"><img :src="value.image" alt="">
                            <div class="preview"><span>Read more</span></div>
                        </a>
                    </figure>
                </div>
                <div class="col-lg-5">
                    <div class="post_info">
                        <small>{{ format_date(value.created_at) }}</small>
                        <h3><a :href="value.slug">{{ value.title }}</a></h3>
                        <p v-html="extractExcerpt(value.content)"></p>
                        <ul>
                            <li>
                                <div class="thumb"><img src="../../public/img/thumb_blog.jpg" alt=""></div> Jessica Hoops
                            </li>
                            <li><i class="icon_comment_alt"></i> {{ value.category.title }}</li>
                        </ul>
                    </div>
                </div>
            </div>
        </article>
        <!-- /article -->        

        
        <paginate
          :page-count="posts.last_page"
          :click-handler="getPosts"
          :prev-text="'Prev'"
          :next-text="'Next'"
          :container-class="'pagination pagination-sm'"
          :page-class="'page-item'"
        >
        </paginate>
        <!-- /pagination -->
    </div>
</template>

<script>
import axios from 'axios'
import moment from 'moment'
import Paginate from "vuejs-paginate-next";



export default {
  data() {
    return {
      posts: []
    }
  },

  components: {
      paginate: Paginate,
    },

  mounted() {
    this.getPosts()
  },

  methods: {
    getPosts(page = 1) {
      axios.get('http://localhost/api/posts?page=' + page).then((res) => {
        this.posts = res.data
        console.log(this.posts)
      })
    },

    format_date(value) {
      if (value) {
        return moment(String(value)).format('DD/MM/YYYY')
      }
    },

    extractExcerpt(text) {
        const words = text.split(' ');
        return words.slice(0, 40).join(' ') + '...';
    }
  }
}
</script>