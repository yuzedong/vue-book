<template>
  <div class="recommend">
    <title-view :label="$t('home.recommend')" :btn="null"></title-view>
    <div class="recommend-list">
      <div
        class="recommend-item"
        v-for="(item, index) in data"
        :key="index"
        @click="showBookDetail(item)"
      >
        <div class="img-wrapper">
          <img class="img" v-lazy="item.cover" />
        </div>
        <div class="content-wrapper">
          <div class="title title-medium" ref="title">{{item.title}}</div>
          <div class="num sub-title" ref="num">{{$t('home.readers').replace('$1', item.readers)}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TitleView from "@/components/home/title";
import { StoreHomeMixin } from "@/mixins/home";
export default {
  name: "Recommend",
  mixins: [StoreHomeMixin],
  components: {
    TitleView
  },
  props: {
    data: Array
  }
};
</script>

<style lang="scss" scoped>
.recommend {
  .recommend-list {
    width: 100%;
    @include top;
    padding: 0 5px;
    box-sizing: border-box;
    .recommend-item {
      flex: 0 0 33.33%;
      width: 33.33%;
      padding: 0 5px;
      box-sizing: border-box;
      .img-wrapper {
        @include center;
        .img {
          width: 80%;
        }
      }
      .content-wrapper {
        width: 100%;
        margin-top: 10px;
        @include columnCenter;
        .title {
          text-align: center;
        }
        .num {
          margin-top: 5px;
        }
      }
    }
  }
}
</style>
