<template>
  <div class="SideNavigation">
    <header class="SideNavigation-HeadingContainer sp-flex">
      <v-icon
        class="SideNavigation-HeadingIcon pc-none"
        :aria-label="$t('サイドメニュー項目を開く')"
        @click="openNavi"
      >
        mdi-menu
      </v-icon>
      <nuxt-link :to="localePath('/')" class="SideNavigation-HeadingLink">
        <h1 class="SideNavigation-Heading">
          <div class="SideNavigation-Logo">
            <img src="/logo.svg" :alt="$t('京都府')" />
          </div>
          京都府<br />
          {{ $t('新型コロナウイルス感染症') }}<br />
          {{ $t('対策サイト') }}
        </h1>
      </nuxt-link>
    </header>
    <v-divider class="SideNavigation-HeadingDivider" />
    <div class="sp-none" :class="{ open: isNaviOpen }">
      <v-icon
        class="SideNavigation-ListContainerIcon pc-none"
        :aria-label="$t('サイドメニュー項目を閉じる')"
        @click="closeNavi"
      >
        mdi-close
      </v-icon>
      <nav>
        <v-list :flat="true">
          <v-container
            v-for="(item, i) in items"
            :key="i"
            class="SideNavigation-ListItemContainer"
            @click="closeNavi"
          >
            <ListItem :link="item.link" :icon="item.icon" :title="item.title" />
            <v-divider v-show="item.divider" class="SideNavigation-Divider" />
          </v-container>
        </v-list>
      </nav>
      <v-footer class="SideNavigation-Footer">
        <small class="SideNavigation-Copyright">
          {{ $t('このサイトの内容物は') }}
          <a
            rel="license"
            target="_blank"
            :href="$t('https://creativecommons.org/licenses/by/4.0/deed.ja')"
          >
            {{ $t('クリエイティブ・コモンズ 表示 4.0 ライセンス') }}
          </a>
          {{ $t('の下に提供されています。') }}
          <br />
        </small>
      </v-footer>
    </div>
  </div>
</template>
<i18n src="./SideNavigation.i18n.json"></i18n>
<script>
import ListItem from '@/components/ListItem'
export default {
  components: {
    ListItem
  },
  props: {
    isNaviOpen: {
      type: Boolean,
      required: true
    }
  },
  computed: {
    items() {
      return [
        {
          icon: 'mdi-chart-timeline-variant',
          title: this.$t('京都府内の最新感染動向'),
          link: this.localePath('/')
        },
        {
          icon: 'parent',
          title: this.$t('お子様をお持ちの皆様へ'),
          link: this.localePath('/parent')
        },
        {
          icon: 'mdi-domain',
          title: this.$t('企業の皆様・はたらく皆様へ'),
          link: this.localePath('/worker'),
          divider: true
        },
        {
          title: this.$t('当サイトについて'),
          link: this.localePath('/about')
        },
        {
          title: this.$t('京都府公式情報'),
          link: 'http://www.pref.kyoto.jp/kentai/news/novelcoronavirus.html'
        },
        {
          title: this.$t('Information about 2019 Novel Coronavirus Infection'),
          link: 'https://www.pref.kyoto.jp/kokusai/coronavirus_update.html'
        },
        {
          title: this.$t('新型冠状病毒感染肺炎相关的信息'),
          link: 'https://www.pref.kyoto.jp/kokusai/coronavirus_cn.html',
          divider: true
        },
        {
          title: this.$t('京都市公式情報'),
          link: 'https://www.city.kyoto.lg.jp/hokenfukushi/page/0000266590.html'
        },
        {
          title: this.$t('福知山市公式情報'),
          link: 'https://www.city.fukuchiyama.lg.jp/site/coronavirus/'
        },
        {
          title: this.$t('舞鶴市公式情報'),
          link: 'https://www.city.maizuru.kyoto.jp/'
        },
        {
          title: this.$t('綾部市公式情報'),
          link:
            'https://www.city.ayabe.lg.jp/bosai/kurashi/anzen/bosai/singatacorona.html'
        },
        {
          title: this.$t('宇治市公式情報'),
          link: 'https://www.city.uji.kyoto.jp/site/corona/'
        },
        {
          title: this.$t('宮津市公式情報'),
          link: 'http://www.city.miyazu.kyoto.jp/'
        },
        {
          title: this.$t('亀岡市公式情報'),
          link: 'https://www.city.kameoka.kyoto.jp/korona-index.html'
        },
        {
          title: this.$t('城陽市公式情報'),
          link: 'https://www.city.joyo.kyoto.jp/'
        },
        {
          title: this.$t('向日市公式情報'),
          link:
            'https://www.city.muko.kyoto.jp/kurashi/kenko_hoken/kenko_iryo/1580171635023.html'
        },
        {
          title: this.$t('長岡京市公式情報'),
          link: 'http://www.city.nagaokakyo.lg.jp/emergencyinfo/0000000084.html'
        },
        {
          title: this.$t('八幡市公式情報'),
          link: 'https://www.city.yawata.kyoto.jp/'
        },
        {
          title: this.$t('京田辺市公式情報'),
          link: 'https://www.kyotanabe.jp/'
        },
        {
          title: this.$t('京丹後市公式情報'),
          link: 'https://www.city.kyotango.lg.jp/kinkyu/korona_all/index.html'
        },
        {
          title: this.$t('南丹市公式情報'),
          link:
            'https://www.city.nantan.kyoto.jp/www/life/113/006/000/index_74314.html'
        },
        {
          title: this.$t('木津川市公式情報'),
          link: 'https://www.city.kizugawa.lg.jp/index.cfm/6,39260,31,296,html'
        },
        {
          title: this.$t('大山崎町公式情報'),
          link: 'https://www.town.oyamazaki.kyoto.jp/'
        },
        {
          title: this.$t('久御山町公式情報'),
          link: 'https://www.town.kumiyama.lg.jp/contents_detail.php?frmId=3421'
        },
        {
          title: this.$t('井手町公式情報'),
          link: 'https://www.town.ide.kyoto.jp/info/1582011890750.html'
        },
        {
          title: this.$t('宇治田原町公式情報'),
          link: 'https://www.town.ujitawara.kyoto.jp/'
        },
        {
          title: this.$t('笠置町公式情報'),
          link:
            'https://www.town.kasagi.lg.jp/contents_detail.php?co=new&frmId=868'
        },
        {
          title: this.$t('和束町公式情報'),
          link:
            'http://www.town.wazuka.lg.jp/contents_detail.php?co=ser&frmId=2747'
        },
        {
          title: this.$t('精華町公式情報'),
          link: 'https://www.town.seika.kyoto.jp/kinkyu_list/12567.html'
        },
        {
          title: this.$t('南山城村公式情報'),
          link: 'http://www.vill.minamiyamashiro.lg.jp/'
        },
        {
          title: this.$t('京丹波町公式情報'),
          link:
            'https://www.town.kyotamba.kyoto.jp/emergencyinfo/0000000041.html'
        },
        {
          title: this.$t('伊根町公式情報'),
          link: 'https://www.town.ine.kyoto.jp/kinkyu/1583369396903.html'
        },
        {
          title: this.$t('与謝野町公式情報'),
          link:
            'https://www.town-yosano.jp/wwwg/info/detail.jsp?common_id=351160',
          divider: true
        },
        {
          title: this.$t('東京都 対策サイト（このサイトの派生元）'),
          link: 'https://stopcovid19.metro.tokyo.lg.jp/',
          divider: true
        }
      ]
    },
    isClass() {
      return item => (item.title.charAt(0) === '【' ? 'kerningLeft' : '')
    }
  },
  methods: {
    openNavi() {
      this.$emit('openNavi')
    },
    closeNavi() {
      this.$emit('closeNavi')
    }
  }
}
</script>

<style lang="scss" scoped>
.SideNavigation {
  position: relative;
  height: 100%;
  background: $white;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.15);
  &-HeadingContainer {
    padding: 1.25em 0 1.25em 1.25em;
    align-items: center;
    @include lessThan($small) {
      padding: 7px 10px;
    }
  }
  &-HeadingIcon {
    margin-right: 10px;
  }
  &-HeadingLink {
    @include lessThan($small) {
      display: flex;
      align-items: center;
    }
    text-decoration: none;
  }
  &-ListContainerIcon {
    width: 21px;
    margin: 24px 16px 0;
  }
  &-ListItemContainer {
    padding: 2px 20px;
  }
  &-Logo {
    margin: 5px 16px 15px 0;
    width: 110px;
    @include lessThan($small) {
      margin: 0 16px 0 0;
    }
  }
  &-Heading {
    margin-top: 8px;
    font-size: 13px;
    color: #898989;
    padding: 0.5em 0;
    text-decoration: none;
    @include lessThan($small) {
      display: flex;
      align-items: center;
      width: 100%;
      margin-top: 0;
    }
  }
  &-HeadingDivider {
    margin: 0px 20px 4px;
    @include lessThan($small) {
      display: none;
    }
  }
  &-Divider {
    margin: 12px 0;
  }
  &-LanguageMenu {
    padding: 0 20px;
    background: #fff;
  }
  &-Footer {
    padding: 20px;
    background-color: $white;
  }
  &-SocialLinkContainer {
    display: flex;
    & a:not(:last-of-type) {
      margin-right: 10px;
    }
    & img {
      width: 30px;
    }
  }
  &-Copyright {
    display: block;
    margin-top: 10px;
    font-size: 8px;
    line-height: 1.2;
    color: $gray-1;
    font-weight: bold;
  }
}
.open {
  @include lessThan($small) {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    display: block !important;
    width: 100%;
    z-index: z-index-of(opened-side-navigation);
    background-color: $white;
    height: 100%;
    overflow-y: scroll;
  }
}
@include lessThan($tiny) {
  .sp-logo {
    width: 100px;
  }
}
@include largerThan($small) {
  .pc-none {
    display: none;
  }
}
@include lessThan($small) {
  .sp-flex {
    display: flex;
  }
  .sp-none {
    display: none;
  }
}
</style>
