<template>
  <v-col cols="12" md="6" class="DataCard">
    <time-bar-chart
      :title="$t('相談人数')"
      :title-id="'number-of-contact'"
      :chart-id="'time-bar-chart-contact'"
      :chart-data="contactsGraph"
      :date="Data.contacts.date"
      :unit="$t('人')"
      :url="'https://www.pref.kyoto.jp/kentai/news/novelcoronavirus.html'"
    />
  </v-col>
</template>

<i18n>
{
  "ja": {
    "相談人数": "相談人数",
    "件": {
      "contact": "件"
    }
  },
  "en": {
    "検査実施人数": "Number of tests conducted",
    "件": {
      "contact": "contacts"
    }
  },
  "zh-cn": {
    "相談人数": "送检件数",
    "件": {
      "contact": "件"
    }
  },
  "zh-tw": {
    "相談人数": "送檢件數",
    "件": {
      "contact": "件"
    }
  },
  "ko": {
    "相談人数": "검사실시수",
    "件": {
      "contact": "건"
    }
  },
  "ja-basic": {
    "検査実施人数": "そうだんした かず",
    "件": {
      "contact": "けん"
    }
  }
}
</i18n>

<script>
import Data from '@/data/data.json'
import formatGraph from '@/utils/formatGraph'
import TimeBarChart from '@/components/TimeBarChart.vue'

export default {
  components: {
    TimeBarChart
  },
  data() {
    // 相談人数グラフ
    const contactsGraph = formatGraph(Data.contacts.data)

    const data = {
      Data,
      contactsGraph
    }
    return data
  }
}
</script>
