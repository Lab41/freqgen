<template>
  <div>
    <b-card-text>
      <b-container>
        <p>
          To get started, we need to know what the target frequencies are. You
          can either use a FASTA file containing DNA sequences as to calculate
          frequencies from, use a Freqgen-generated YAML file with precalculated
          frequencies, or manually enter frequencies.
        </p>
      </b-container>
      <b-container>
        <b-form-textarea
          id="textarea"
          v-model="aminoAcidSeq"
          placeholder="Paste YAML here..."
          rows="3"
          max-rows="6"
          :disabled="Boolean(file)"
        ></b-form-textarea>
        <p class="text-center my-3">or</p>
        <b-row>
          <b-col cols="10">
            <b-form-file
              v-model="file"
              :state="Boolean(file) ? true : null"
              placeholder="Choose a file or drop it here..."
              drop-placeholder="Drop file here..."
              accept=".yml, .yaml"
            ></b-form-file>
          </b-col>
          <b-col cols="2">
            <b-button
              variant="outline-secondary"
              block
              :disabled="!Boolean(file)"
              @click="file = []"
            >Clear file</b-button>
          </b-col>
        </b-row>
      </b-container>
    </b-card-text>
  </div>
</template>

<script>
export default {
  name: 'TargetAminoAcid',
  data() {
    return {
      file: null,
    }
  },
  computed: {
    aminoAcidSeq: {
      get() {
        return this.$store.state.aminoAcidSeq
      },
      set(value) {
        this.$store.commit('setAminoAcidSeq', value)
      },
    },
  },
}
</script>

<style>
</style>