<template>
  <modal-inner class="modal__inner-1--about-modal" aria-label="About">
    <div class="modal__content">
      <div class="logo-background"></div>
      PawnMD on <a target="_blank" href="https://github.com/fortembr/pawn-markdown/">GitHub</a>
      <br>
      <a target="_blank" href="https://github.com/fortembr/pawn-markdown/issues">Issue tracker</a> — <a target="_blank" href="https://github.com/fortembr/pawn-markdown/releases">Changelog</a>
      <br>
      <a target="_blank" href="https://fortembr.com/discord/">Community</a> — <a target="_blank" href="https://community.stackedit.io/c/how-to">Tutos and How To</a>
      <br>
      PawnMD on <a target="_blank" href="https://twitter.com/fortembr/">Twitter</a>
      <hr>
      <small>© 2013-2019 Dock5 Software Ltd.<br>v{{version}}</small>
      <h3>FAQ</h3>
      <div class="faq" v-html="faq"></div>
      <div class="modal__info">
        For commercial support or custom development, please <a href="mailto:hello@fortembr.com">contact us</a>.
      </div>
      <a target="_blank" href="http://www.apache.org/licenses/LICENSE-2.0">Apache License</a><br>
      <a target="_blank" href="https://fortembr.com/legal/privacy-policy/">Privacy Policy</a>
    </div>
    <div class="modal__button-bar">
      <button class="button button--resolve" @click="config.resolve()">Close</button>
    </div>
  </modal-inner>
</template>

<script>
import { mapGetters } from 'vuex';
import ModalInner from './common/ModalInner';
import markdownConversionSvc from '../../services/markdownConversionSvc';
import faq from '../../data/faq.md';

export default {
  components: {
    ModalInner,
  },
  data: () => ({
    version: VERSION,
  }),
  computed: {
    ...mapGetters('modal', ['config']),
    faq() {
      return markdownConversionSvc.defaultConverter.render(faq);
    },
  },
};
</script>

<style lang="scss">
.modal__inner-1--about-modal {
  text-align: center;

  .logo-background {
    height: 75px;
    margin: 0.5em 0;
  }

  small {
    display: block;
  }

  hr {
    width: 160px;
    max-width: 100%;
    margin: 1.5em auto;
  }
}

.faq {
  font-size: 0.8em;
  line-height: 1.5;
}
</style>
