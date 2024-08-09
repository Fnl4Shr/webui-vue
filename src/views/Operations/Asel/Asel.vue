<template>
  <b-container fluid="xl">
    <page-title />
    <b-row>
      <b-col md="8" lg="8" xl="6">
        <page-section>
          {{ $t('pageAsel.information') }}
          <b-button
            variant="primary"
            class="d-block mt-5"
            data-test-id="pageAsel-runScript-button"
            @click="onClick"
          >
            {{ $t('pageAsel.runScript') }}
          </b-button>
        </page-section>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import PageTitle from '@/components/Global/PageTitle';
import PageSection from '@/components/Global/PageSection';
import BVToastMixin from '@/components/Mixins/BVToastMixin';
import LoadingBarMixin from '@/components/Mixins/LoadingBarMixin';

export default {
  name: 'RunAselScript',
  components: { PageTitle, PageSection },
  mixins: [BVToastMixin, LoadingBarMixin],
  methods: {
    onClick() {
      this.runAselScript();
    },
    runAselScript() {
      this.$store
        .dispatch('controls/runAselScript')
        .then((message) => this.successToast(message))
        .catch(({ message }) => this.errorToast(message));
    },
  },
};
</script>

<style lang="scss" scoped></style>
