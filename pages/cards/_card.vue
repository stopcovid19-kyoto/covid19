<template>
  <div>
    <confirmed-cases-number-card
      v-if="this.$route.params.card == 'number-of-confirmed-cases'"
    />
    <confirmed-cases-attributes-card
      v-else-if="this.$route.params.card == 'attributes-of-confirmed-cases'"
    />
    <tested-number-card
      v-else-if="this.$route.params.card == 'number-of-tested'"
    />
    <confirmed-cases-details-card
      v-else-if="this.$route.params.card == 'details-of-confirmed-cases'"
    />
    <contact-number-card
      v-else-if="this.$route.params.card == 'number-of-contact'"
    />
  </div>
</template>

<i18n>
{
  "ja": {
    "検査陽性者の状況": "検査陽性者の状況",
    "陽性患者数": "陽性患者数",
    "陽性患者の属性": "陽性患者の属性",
    "検査実施人数": "検査実施人数"
  },
  "en": {
    "検査陽性者の状況": "Details of confirmed cases",
    "陽性患者数": "Number of confirmed cases",
    "陽性患者の属性": "Confirmed patient attributes",
    "検査実施人数": "Number of tests conducted"
  },
  "zh-cn": {
    "検査陽性者の状況": "确诊案例状况",
    "陽性患者数": "确诊人数",
    "陽性患者の属性": "确诊患者的信息",
    "検査実施人数": "送检件数"
  },
  "zh-tw": {
    "検査陽性者の状況": "確診案例狀況",
    "陽性患者数": "確診人數",
    "陽性患者の属性": "確診案例概況",
    "検査実施人数": "送檢件數"
  },
  "ko": {
    "検査陽性者の状況": "확진자의 현황",
    "陽性患者数": "확진자 수",
    "陽性患者の属性": "확진 사례의 세부 사항",
    "検査実施人数": "검사실시수"
  },
  "ja-basic": {
    "検査陽性者の状況": "びょうきの ひとは いま",
    "陽性患者数": "びょうきの ひとの かず",
    "陽性患者の属性": "びょうきの ひとの じょうほう",
    "検査実施人数": "けんさした かず"
  }
}
</i18n>

<script>
import Data from '@/data/data.json'
import ConfirmedCasesDetailsCard from '@/components/cards/ConfirmedCasesDetailsCard.vue'
import ConfirmedCasesNumberCard from '@/components/cards/ConfirmedCasesNumberCard.vue'
import ConfirmedCasesAttributesCard from '@/components/cards/ConfirmedCasesAttributesCard.vue'
import TestedNumberCard from '@/components/cards/TestedNumberCard.vue'
import ContactNumberCard from '@/components/cards/ContactNumberCard.vue'

export default {
  components: {
    ConfirmedCasesDetailsCard,
    ConfirmedCasesNumberCard,
    ConfirmedCasesAttributesCard,
    TestedNumberCard,
    ContactNumberCard
  },
  data() {
    let title, updatedAt
    switch (this.$route.params.card) {
      case 'details-of-confirmed-cases':
        title = this.$t('検査陽性者の状況')
        updatedAt = Data.inspections_summary.date
        break
      case 'number-of-confirmed-cases':
        title = this.$t('陽性患者数')
        updatedAt = Data.patients.date
        break
      case 'attributes-of-confirmed-cases':
        title = this.$t('陽性患者の属性')
        updatedAt = Data.patients.date
        break
      case 'number-of-tested':
        title = this.$t('検査実施人数')
        updatedAt = Data.inspections_summary.date
        break
      case 'number-of-contact':
        title = this.$t('専用相談窓口 相談件数')
        updatedAt = Data.contact.date
        break
    }

    const data = {
      title,
      updatedAt
    }
    return data
  },
  head() {
    const url = 'https://stopcovid19-kyoto.netlify.com'
    const timestamp = new Date().getTime()
    const ogpImage =
      url +
      '/ogp/' +
      this.$i18n.locale +
      '/' +
      this.$route.params.card +
      '.png?t=' +
      timestamp
    const description =
      this.updatedAt +
      ' | ' +
      this.$t(
        '当サイトは新型コロナウイルス感染症（COVID-19）に関する最新情報を提供するために、有志が集まり開設したものです。'
      )

    return {
      title: this.title,
      meta: [
        {
          hid: 'og:url',
          property: 'og:url',
          content: url + this.$route.path + '/'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content:
            this.title +
            ' | ' +
            this.$t('京都府') +
            ' ' +
            this.$t('新型コロナウイルス感染症') +
            this.$t('対策サイト')
        },
        {
          hid: 'description',
          name: 'description',
          content: description
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: description
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: ogpImage
        },
        {
          hid: 'twitter:image',
          name: 'twitter:image',
          content: ogpImage
        }
      ]
    }
  }
}
</script>
