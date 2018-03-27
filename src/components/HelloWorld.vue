<template>
  <div class="hello">
    <div class='container-fluid filter-container'>
      <div class='row filters'>
        <div class='col-12'>
          <input type='text' class='search form-control' placeholder='Search' v-model='searchTerm' />
         </div>
      </div>
    </div>

    <div class='container'>
      <div class='row text-left'>
        <div class='col-12 col-md-4' v-for='resource in resources'>
          <div class='card'>

            <div class='img' :style='`background-image: url("${resource.img}")`'></div>

            <strong>{{resource.title}}</strong>

            <p>{{resource.desc.substr(0, 100)}} ...</p>

            <!-- <div class='tags'>
              <b-badge pill variant="primary">{{resource.tags[0]}}</b-badge>
              <b-badge pill variant="secondary">{{resource.format[0]}}</b-badge>
            </div> -->

            <div class='share'>
          		<a :href="`https://telegram.me/share/url?url=${resource.link}`" target="_blank">
                <svg class="svg-inline--fa fa-telegram-plane fa-w-14" aria-hidden="true" data-fa-processed="" data-prefix="fab" data-icon="telegram-plane" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path fill="currentColor" d="M446.7 98.6l-67.6 318.8c-5.1 22.5-18.4 28.1-37.3 17.5l-103-75.9-49.7 47.8c-5.5 5.5-10.1 10.1-20.7 10.1l7.4-104.9 190.9-172.5c8.3-7.4-1.8-11.5-12.9-4.1L117.8 284 16.2 252.2c-22.1-6.9-22.5-22.1 4.6-32.7L418.2 66.4c18.4-6.9 34.5 4.1 28.5 32.2z"></path></svg><!-- <i class="fab fa-telegram-plane"></i> -->
              </a>
              <a :href="`http://www.reddit.com/submit?url=${resource.link}`" target="_blank">
                <svg class="svg-inline--fa fa-reddit-alien fa-w-16" aria-hidden="true" data-fa-processed="" data-prefix="fab" data-icon="reddit-alien" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M440.3 203.5c-15 0-28.2 6.2-37.9 15.9-35.7-24.7-83.8-40.6-137.1-42.3L293 52.3l88.2 19.8c0 21.6 17.6 39.2 39.2 39.2 22 0 39.7-18.1 39.7-39.7s-17.6-39.7-39.7-39.7c-15.4 0-28.7 9.3-35.3 22l-97.4-21.6c-4.9-1.3-9.7 2.2-11 7.1L246.3 177c-52.9 2.2-100.5 18.1-136.3 42.8-9.7-10.1-23.4-16.3-38.4-16.3-55.6 0-73.8 74.6-22.9 100.1-1.8 7.9-2.6 16.3-2.6 24.7 0 83.8 94.4 151.7 210.3 151.7 116.4 0 210.8-67.9 210.8-151.7 0-8.4-.9-17.2-3.1-25.1 49.9-25.6 31.5-99.7-23.8-99.7zM129.4 308.9c0-22 17.6-39.7 39.7-39.7 21.6 0 39.2 17.6 39.2 39.7 0 21.6-17.6 39.2-39.2 39.2-22 .1-39.7-17.6-39.7-39.2zm214.3 93.5c-36.4 36.4-139.1 36.4-175.5 0-4-3.5-4-9.7 0-13.7 3.5-3.5 9.7-3.5 13.2 0 27.8 28.5 120 29 149 0 3.5-3.5 9.7-3.5 13.2 0 4.1 4 4.1 10.2.1 13.7zm-.8-54.2c-21.6 0-39.2-17.6-39.2-39.2 0-22 17.6-39.7 39.2-39.7 22 0 39.7 17.6 39.7 39.7-.1 21.5-17.7 39.2-39.7 39.2z"></path></svg><!-- <i class="fab fa-reddit-alien"></i> -->
              </a>
              <a :href="`https://twitter.com/home?status=${resource.link}`" target="_blank"><svg class="svg-inline--fa fa-twitter fa-w-16" aria-hidden="true" data-fa-processed="" data-prefix="fab" data-icon="twitter" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M459.37 151.716c.325 4.548.325 9.097.325 13.645 0 138.72-105.583 298.558-298.558 298.558-59.452 0-114.68-17.219-161.137-47.106 8.447.974 16.568 1.299 25.34 1.299 49.055 0 94.213-16.568 130.274-44.832-46.132-.975-84.792-31.188-98.112-72.772 6.498.974 12.995 1.624 19.818 1.624 9.421 0 18.843-1.3 27.614-3.573-48.081-9.747-84.143-51.98-84.143-102.985v-1.299c13.969 7.797 30.214 12.67 47.431 13.319-28.264-18.843-46.781-51.005-46.781-87.391 0-19.492 5.197-37.36 14.294-52.954 51.655 63.675 129.3 105.258 216.365 109.807-1.624-7.797-2.599-15.918-2.599-24.04 0-57.828 46.782-104.934 104.934-104.934 30.213 0 57.502 12.67 76.67 33.137 23.715-4.548 46.456-13.32 66.599-25.34-7.798 24.366-24.366 44.833-46.132 57.827 21.117-2.273 41.584-8.122 60.426-16.243-14.292 20.791-32.161 39.308-52.628 54.253z"></path></svg><!-- <i class="fab fa-twitter"></i> -->
              </a>
              <a :href="`https://www.facebook.com/sharer/sharer.php?u=${resource.link}`" target="_blank"><svg class="svg-inline--fa fa-facebook-f fa-w-9" aria-hidden="true" data-fa-processed="" data-prefix="fab" data-icon="facebook-f" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 264 512"><path fill="currentColor" d="M76.7 512V283H0v-91h76.7v-71.7C76.7 42.4 124.3 0 193.8 0c33.3 0 61.9 2.5 70.2 3.6V85h-48.2c-37.8 0-45.1 18-45.1 44.3V192H256l-11.7 91h-73.6v229"></path></svg><!-- <i class="fab fa-facebook-f"></i> -->
              </a>
              <a :href="`mailto:?subject=${resource.link}`"><svg class="svg-inline--fa fa-envelope-open fa-w-16" aria-hidden="true" data-fa-processed="" data-prefix="far" data-icon="envelope-open" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="currentColor" d="M494.586 164.516c-4.697-3.883-111.723-89.95-135.251-108.657C337.231 38.191 299.437 0 256 0c-43.205 0-80.636 37.717-103.335 55.859-24.463 19.45-131.07 105.195-135.15 108.549A48.004 48.004 0 0 0 0 201.485V464c0 26.51 21.49 48 48 48h416c26.51 0 48-21.49 48-48V201.509a48 48 0 0 0-17.414-36.993zM464 458a6 6 0 0 1-6 6H54a6 6 0 0 1-6-6V204.347c0-1.813.816-3.526 2.226-4.665 15.87-12.814 108.793-87.554 132.364-106.293C200.755 78.88 232.398 48 256 48c23.693 0 55.857 31.369 73.41 45.389 23.573 18.741 116.503 93.493 132.366 106.316a5.99 5.99 0 0 1 2.224 4.663V458zm-31.991-187.704c4.249 5.159 3.465 12.795-1.745 16.981-28.975 23.283-59.274 47.597-70.929 56.863C336.636 362.283 299.205 400 256 400c-43.452 0-81.287-38.237-103.335-55.86-11.279-8.967-41.744-33.413-70.927-56.865-5.21-4.187-5.993-11.822-1.745-16.981l15.258-18.528c4.178-5.073 11.657-5.843 16.779-1.726 28.618 23.001 58.566 47.035 70.56 56.571C200.143 320.631 232.307 352 256 352c23.602 0 55.246-30.88 73.41-45.389 11.994-9.535 41.944-33.57 70.563-56.568 5.122-4.116 12.601-3.346 16.778 1.727l15.258 18.526z"></path></svg><!-- <i class="far fa-envelope-open"></i> -->
              </a>
            </div>

            <a :href='resource.link' target='_blank' class='btn btn-primary'>View</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ModelSelect } from 'vue-search-select';

export default {
  name: 'HelloWorld',
  components: {
    ModelSelect,
  },
  metaInfo() {
    const title = 'Ologies Podcast';

    return {
      title,
      meta: [
        { vmid: 'description', name: 'description', content: title },
      ],
    };
  },
  data() {
    return {
      msg: 'Machine Learning Tutorials',
      searchTerm: '',
      catOptions: [
        { value: 'Linear Algebra', text: 'Linear Algebra' },
        { value: 'Convex Optimization', text: 'Convex Optimization' },
        { value: 'Statistics', text: 'Statistics' },
        { value: 'Differential Equations & Calculus', text: 'Differential Equations & Calculus' },
        { value: 'Data Mining', text: 'Data Mining' },
        { value: 'General Machine Learning', text: 'General Machine Learning' },
        { value: 'Reinforcement Learning', text: 'Reinforcement Learning' },
        { value: 'Deep Learning', text: 'Deep Learning' },
        { value: 'Convolutional Neural Networks', text: 'Convolutional Neural Networks' },
        { value: 'Recurrent Neural Networks', text: 'Recurrent Neural Networks' },
      ],
      selectedCat: {
        value: '',
        text: '',
      },
      formatOptions: [
        { value: 'Book', text: 'Book' },
        { value: 'Website', text: 'Website' },
        { value: 'Video', text: 'Video' },
      ],
      selectedFormat: {
        value: '',
        text: '',
      },
    };
  },
  computed: {
    resources() {
      const result = this.$store.getters.filterItems(this.searchTerm);
      return result;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }

  h2 {
    margin-top: 2em;
    margin-bottom: 2em;
  }

  .search {
    border: none;
  }

  .filter-container {
    /* background: linear-gradient(to right, #E100FF, #0066ff); */
    background-color: #f9f7e3;
  }

  .filters {
    margin-bottom: 2em;
    max-width: 1140px;
    margin: 0 auto;
    padding-top: 1em;
    padding-bottom: 1em;
    margin-bottom: 1em;
  }

  .card {
    padding: 1em;
    min-height: 380px;
    background-color: #fff;
    box-shadow: 0 4px 30px 0 rgba(223,225,230,0.5);
    border-radius: 10px;
    margin-bottom: 1em;
    border: none;
  }

  .card .img {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background-position: center;
    background-size: contain;
  }

  .badge-primary {
    /* background: #FF6D4A; */
  }

  .badge {
    font-size: 14px;
    margin-bottom: 10px;
    cursor: pointer;
    display: inline-block;
    background-color: #fafafa;
    padding: 5px 10px;
    border-radius: 40px;
    color: #ccc;
    text-transform: lowercase;
  }

  .btn-primary {
    color: #999 !important;
    margin-right: 10px;
    border: 1px solid #f3f3f3;
    text-transform: uppercase;
    border-radius: 40px;
    padding: 5px 10px;
    font-weight: 600;
    font-size: 11px;
    background-color: #f9f7e3;
  }

  strong {
    /* color: #FF6D4A; */
    font-family: 'Poppins', sans-serif;
    margin-top: .5em;
    margin-bottom: .5em;
    font-size: 20px;
    font-weight: bold;
    color: #000;
  }

  a {
    color: #fff !important;
    width: 80px;
    position: absolute;
    bottom: 10px;
  }

  .share {
    width: 100%;
    margin-top: 1em;
  }

  .share a svg {
    height: 15px;
  }

  .share a {
    color: #ccc !important;
    width: 15px;
    height: 15px;
    display: inline-block;
    position: relative;
    margin-right: .5em;
  }
</style>
