<template>
  <v-col cols="12" md="6" class="DataCard">
    <time-bar-chart
      :title="$t('検査実施人数')"
      :title-id="'number-of-tested'"
      :chart-id="'time-bar-chart-inspections'"
      :chart-data="inspectionsGraph"
      :date="Data.inspections.date"
      :unit="$t('人')"
      :url="'https://www.pref.kyoto.jp/kentai/corona/pcrkensa.html'"
    />
    <!-- 
    <time-stacked-bar-chart
      :title="$t('検査実施人数')"
      :title-id="'number-of-tested'"
      :chart-id="'time-stacked-bar-chart-inspections'"
      :chart-data="inspectionsGraph"
      :date="Data.inspections_summary.date"
      :items="inspectionsItems"
      :labels="inspectionsLabels"
      :unit="$t('件.tested')"
      :url="'https://www.pref.kyoto.jp/kentai/corona/pcrkensa.html'"
    />
    -->
    <!--  :url="https://www.mhlw.go.jp/stf/seisakunitsuite/bunya/0000164708_00001.html'" -->
    <!-- :url="'https://www.pref.kyoto.jp/kentai/news/novelcoronavirus.html#F'" -->
    <!-- :url="'https://code4sabae.github.io/covid19/index.html'" -->
    <!-- 件.tested = 検査数 -->
  </v-col>
</template>

<i18n>
{
  "ja": {
    "検査実施人数": "検査実施人数",
    "府内": "府内",
    "府内発生": "府内発生",
    "その他（チャーター便・クルーズ船）": "その他（チャーター便・クルーズ船）",
    "件": {
      "tested": "件"
    }
  },
  "en": {
    "検査実施人数": "Number of tests conducted",
    "府内発生": "Emerged in Tokyo (Suspected cases or contactees)",
    "その他（チャーター便・クルーズ船）": "Others (Returnees or Cruise ship passengers)",
    "件": {
      "tested": "cases"
    }
  },
  "zh-cn": {
    "検査実施人数": "送检件数",
    "府内発生": "东京都案例（疑似感染、接触者调查）",
    "その他（チャーター便・クルーズ船）": "其它（包机、游轮）",
    "件": {
      "tested": "件"
    }
  },
  "zh-tw": {
    "検査実施人数": "送檢件數",
    "府内発生": "東京都案例（疑似感染、接觸者調查）",
    "その他（チャーター便・クルーズ船）": "其它（包機、遊輪）",
    "件": {
      "tested": "件"
    }
  },
  "ko": {
    "検査実施人数": "검사실시수",
    "府内発生": "도쿄 지역사회 발생 경우（의심환자, 접촉자）",
    "その他（チャーター便・クルーズ船）": "기타（귀국자 또는 크루즈 승객 경우）",
    "件": {
      "tested": "건"
    }
  },
  "ja-basic": {
    "検査実施人数": "けんさした かず",
    "府内発生": "とうきょうとで びょうき かもしれない ひと",
    "その他（チャーター便・クルーズ船）": "そのほか",
    "件": {
      "tested": "けん"
    }
  }
}
</i18n>

<script>
import Data from '@/data/data.json'
import formatGraph from '@/utils/formatGraph'
// import TimeStackedBarChart from '@/components/TimeStackedBarChart.vue'
import TimeBarChart from '@/components/TimeBarChart.vue'

export default {
  components: {
    // TimeStackedBarChart
    TimeBarChart
  },
  data() {
    //  // 検査実施日別状況
    //  // const inspectionsGraph = [
    //  //  Data.inspections_summary.data['府内']
    //    // Data.inspections_summary.data['府内'],
    //    // Data.inspections_summary.data['その他']
    //  // ]
    //  const inspectionsGraph = formatGraph(Data.inspections.data)
    //  const inspectionsItems = [
    //    this.$t('府内発生（疑い例・接触者調査）'),
    //    // this.$t('府内発生（疑い例・接触者調査）')
    //    // this.$t('その他（チャーター便・クルーズ船）')
    //  ]
    //  const inspectionsLabels = Data.inspections_summary.labels

    // 検査人数グラフ
    const inspectionsGraph = formatGraph(Data.inspections.data)

    const data = {
      Data,
      inspectionsGraph
      // inspectionsItems,
      // inspectionsLabels
    }
    return data
  }
}
</script>
