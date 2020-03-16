<template>
  <div class="Worker">
    <h2 class="Worker-Heading">
      {{ $t('企業の皆様・はたらく皆様へ') }}
    </h2>
    <div v-for="(item, i) in items" :key="i">
      <TextCard
        :title="$t(item.title)"
        :link="item.link"
        :body="$t(item.body)"
      />
    </div>
  </div>
</template>

<i18n src="./worker.i18n.json"></i18n>

<script lang="ts">
import TextCard from '@/components/TextCard.vue'

export default {
  components: {
    TextCard
  },
  data() {
    return {
      items: [
        {
          title: '相談窓口',
          link: 'http://www.pref.kyoto.jp/kentai/news/novelcoronavirus.html#E',
          body: '中小企業・小規模事業者の方を対象とした相談窓口です。'
        },
        {
          title: '宿泊施設の方へ',
          link: 'http://www.pref.kyoto.jp/kentai/news/novelcoronavirus.html#D',
          body: '宿泊施設の方へのご案内です。'
        },
        {
          title: '労働相談窓口',
          link: 'http://www.pref.kyoto.jp/rosei/20200301roudousoudan.html',
          body: '新型コロナウイルス感染症に関する労働相談窓口などのご案内です。'
        }
      ]
    }
  },
  head() {
    return {
      title: '企業の皆様・はたらく皆様へ'
    }
  }
}
</script>

<style lang="scss">
.Worker {
  &-Heading {
    @include font-size(30);
    font-weight: normal;
    color: $gray-2;
    margin-bottom: 12px;
  }
}
</style>
