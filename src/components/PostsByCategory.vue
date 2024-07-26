<template>
    <div class="col-lg-9">
        <article class="blog "
                v-for="value in categories.posts" :key="value">
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
                        <h3><a :href="'/'+value.slug">{{ value.title }}</a></h3>
                        <p v-html="extractExcerpt(value.content)"></p>
                        <ul>
                            <li>
                                <div class="thumb"><img src="../../public/img/thumb_blog.jpg" alt=""></div> Jessica Hoops
                            </li>
                            <li><i class="icon_comment_alt"></i> {{ categories.title }}</li>
                        </ul>
                    </div>
                </div>
            </div>
        </article>
        <!-- /article -->        

        <nav aria-label="...">
            <ul class="pagination pagination-sm">
                <li class="page-item disabled">
                    <a class="page-link" href="#" tabindex="-1">Previous</a>
                </li>
                <li class="page-item"><a class="page-link" href="#">1</a></li>
                <li class="page-item"><a class="page-link" href="#">2</a></li>
                <li class="page-item"><a class="page-link" href="#">3</a></li>
                <li class="page-item">
                    <a class="page-link" href="#">Next</a>
                </li>
            </ul>
        </nav>
        <!-- /pagination -->
    </div>
</template>

<script>
import axios from 'axios'
import moment from 'moment'

export default {
  data() {
    return {
      categories: []
    }
  },

  mounted() {
    this.getCategories()
  },

  methods: {
    getCategories() {

      const urlFull = window.location.href
      const urlParts = urlFull.split('/')

      const slug = urlParts[urlParts.length - 1]
    //   console.log(slug);

      axios.get(`http://localhost/api/category/${slug}`).then((res) => {
        this.categories = res.data
        console.log(this.categories)
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