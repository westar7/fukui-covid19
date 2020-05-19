<template>
  <div class="MainPage">
    <page-header
      :icon="headerItem.icon"
      :title="headerItem.title"
      :date="headerItem.date"
    />
    <whats-new class="mb-4" :items="newsItems" />


<div class="row DataBlock">

  <div class="DataCard col-md-6 col-12">
    <div class="WhatsNew" style="height:100%">
      <h3 class="WhatsNew-heading"><i aria-hidden="true" class="v-icon notranslate WhatsNew-heading-icon mdi mdi-information theme--light" style="font-size:24px;"></i>
          県内の重要なニュース
        </h3>
      <div class="TopNews">
      <span class="TopNewsImp2">感染者・濃厚接触者や医療従事者ならびにその家族や関係者等に対して、いわれのない誹謗中傷や差別的行為は絶対しないようお願いします。（福井県 県民行動指針ver.4より一部抜粋）</span><br>
      <br>
      <span class="TopNewsImp3">【5/18】6月1日から県内の小中学校の授業を再開</span><br>
      <span class="TopNewsImp3">【5/15】6月1日から県立学校の授業を再開 <a href="https://www.pref.fukui.lg.jp/doc/kenkou/covid19_honb_d/fil/200515.pdf" target="_blank">詳しくはこちら</a></span><br>
      <span class="TopNewsImp3">【5/14】政府が39県の「緊急事態宣言」を解除（福井県も含まれる）</span><br>
      【5/5】福井県から5月20日までの県民の外出自粛、休業要請、学校再開などについて発表がありました <a href="https://www.pref.fukui.lg.jp/doc/kenkou/covid19_honb_d/fil/200505.pdf" target="_blank">詳しくはこちら</a>
      </div>
    </div>
  </div>

  <div class="DataCard col-md-6 col-12">
    <div class="WhatsNew" style="height:100%">
      <h3 class="WhatsNew-heading"><i aria-hidden="true" class="v-icon notranslate WhatsNew-heading-icon mdi mdi-information theme--light" style="font-size:24px;"></i>
        県民行動指針ver.4 <a class="TopNews" href="https://www.pref.fukui.lg.jp/doc/kenkou/covid19_chiji_d/fil/200517.pdf" target="_blank">詳しくはこちら</a>
      </h3>
      <div class="TopNews">
      1.感染防止対策を徹底<br>
      2.緊急事態宣言の対象地域など他県との往来を自粛<br>
      3.感染リスクが高まる密閉・密集・密接の場を「つくらない」「近づかない」<br>
      4.医療機関を受信する前に電話で相談<br>
      5.職場における感染防止対策を徹底する<br>
      6.店舗等における感染防止対策を徹底する<br>
      7.県内医療を守るために最大限協力する<br>
      8.人権・個人情報保護を徹底する
      </div>
    </div>
  </div>

</div>

    <static-info
      class="mb-4"
      url="https://www.pref.fukui.lg.jp/doc/kouho/navi.html"
      target="_blank"
      :text="$t('自分や家族の症状に不安や心配があればまずは電話相談をどうぞ')"
      :btn-text="$t('相談の手順を見る')"
    />
    <v-row class="DataBlock">
      <confirmed-cases-details-card />
      <confirmed-cases-number-card />
      <confirmed-cases-attributes-card />
      <tested-number-card />
    </v-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { MetaInfo } from 'vue-meta'
import PageHeader from '@/components/PageHeader.vue'
import WhatsNew from '@/components/WhatsNew.vue'
import StaticInfo from '@/components/StaticInfo.vue'
import Data from '@/data/data.json'
import News from '@/data/news.json'
import ConfirmedCasesDetailsCard from '@/components/cards/ConfirmedCasesDetailsCard.vue'
import ConfirmedCasesNumberCard from '@/components/cards/ConfirmedCasesNumberCard.vue'
import ConfirmedCasesAttributesCard from '@/components/cards/ConfirmedCasesAttributesCard.vue'
import TestedNumberCard from '@/components/cards/TestedNumberCard.vue'
import TelephoneAdvisoryReportsNumberCard from '@/components/cards/TelephoneAdvisoryReportsNumberCard.vue'
import ConsultationDeskReportsNumberCard from '@/components/cards/ConsultationDeskReportsNumberCard.vue'
import MetroCard from '@/components/cards/MetroCard.vue'
import AgencyCard from '@/components/cards/AgencyCard.vue'

export default Vue.extend({
  components: {
    PageHeader,
    WhatsNew,
    StaticInfo,
    ConfirmedCasesDetailsCard,
    ConfirmedCasesNumberCard,
    ConfirmedCasesAttributesCard,
    TestedNumberCard,
    TelephoneAdvisoryReportsNumberCard,
    ConsultationDeskReportsNumberCard,
    MetroCard,
    AgencyCard
  },
  data() {
    const data = {
      Data,
      headerItem: {
        icon: 'mdi-chart-timeline-variant',
        title: this.$t('福井県内の最新感染動向'),
        date: Data.lastUpdate
      },
      newsItems: News.newsItems
    }
    return data
  },
  head(): MetaInfo {
    return {
      title: this.$t('福井県内の最新感染動向') as string
    }
  }
})
</script>

<style lang="scss" scoped>
.TopNews {
  font-size: 13px;
  line-height: 1.8em;
  padding: 0 10px;
}
.TopNewsImp {
  font-size: 14px;
  font-weight: bold;
  text-decoration: underline;
  color: red;
}
.TopNewsImp2 {
  font-size: 14px;
  color: red;
}
.TopNewsImp3 {
  font-size: 14px;
  color: red;
  text-decoration: underline;
}
.MainPage {
  .DataBlock {
    margin: 20px -8px;
    .DataCard {
      @include largerThan($medium) {
        padding: 10px;
      }
      @include lessThan($small) {
        padding: 4px 8px;
      }
    }
  }
}
</style>
