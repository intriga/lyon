<template>
    <aside class="col-lg-3">
        <div class="widget">
            <form>
                <div class="form-group">
                    <input type="text" name="search" id="search" class="form-control" placeholder="Search...">
                </div>
                <button type="submit" id="submit" class="btn_1 rounded"> Search</button>
            </form>
        </div>
        <!-- /widget -->
        <!-- <div class="widget">
            <div class="widget-title">
                <h4>Recent Posts</h4>
            </div>
            <ul class="comments-list">
                <li>
                    <div class="alignleft">
                        <a href="#0"><img src="../../public/img/blog-5.jpg" alt=""></a>
                    </div>
                    <small>11.08.2016</small>
                    <h3><a href="#" title="">Verear qualisque ex minimum...</a></h3>
                </li>
                <li>
                    <div class="alignleft">
                        <a href="#0"><img src="../../public/img/blog-6.jpg" alt=""></a>
                    </div>
                    <small>11.08.2016</small>
                    <h3><a href="#" title="">Verear qualisque ex minimum...</a></h3>
                </li>
                <li>
                    <div class="alignleft">
                        <a href="#0"><img src="../../public/img/blog-4.jpg" alt=""></a>
                    </div>
                    <small>11.08.2016</small>
                    <h3><a href="#" title="">Verear qualisque ex minimum...</a></h3>
                </li>
            </ul>
        </div> -->
        <!-- /widget -->
        <div class="widget">
            <div class="widget-title">
                <h4>Blog Categories</h4>
            </div>
            <ul class="cats"
                v-for="value in categories" :key="value">
                <li><a :href="value.slug">{{ value.title }}</a></li>
            </ul>
        </div>
        <!-- /widget -->
        <div class="widget">
            <div class="widget-title">
                <h4>Popular Tags</h4>
            </div>
            <div class="tags">
                <a href="#">Information tecnology</a>
                <a href="#">Students</a>
                <a href="#">Community</a>
                <a href="#">Carreers</a>
                <a href="#">Literature</a>
                <a href="#">Seminars</a>
            </div>
        </div>
        <!-- /widget -->
    </aside>
</template>

<script>
    import axios from 'axios';
    import moment from 'moment';

    export default {

        data() {
            return {
                categories: []
            }
        },

        mounted() {
            this.getCategories();
        },

        methods: {
            getCategories() {
                axios.get('http://localhost/api/categories').then(res => {
                    this.categories = res.data;
                    //console.log(this.categories);
                });
            },

            format_date(value) {
                if (value) {
                    return moment(String(value)).format('DD/MM/YYYY');
                }
            }

        }
    }
</script>