<template>
    <el-carousel :interval="4000" type="card" height="200px">
        <el-carousel-item v-for="(movie, index) in availbleMovies">
            <a @click.prevent.stop="PlayMovie(index)"><img :src="movie.poster" class="image"></a>
            <div style="padding: 14px;">
                <span>{{ movie.name }}</span>
                <div class="bottom clearfix">
                <time class="time">{{ movie.year }}</time>
                <el-button type="text" class="button">Operating button</el-button>
                </div>
            </div>
        </el-carousel-item>
    </el-carousel>
</template>

<script>
export default {
  name: 'PlayerFooter',
  props: ['availbleMovies'],
  methods: {
    PlayMovie: function (index) {
      this.$emit('selectMovie', {index: index});
    }
  }
}
</script>

<style>
  .time {
    font-size: 13px;
    color: #999;
  }
  
  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
      display: table;
      content: "";
  }
  
  .clearfix:after {
      clear: both
  }
</style>
