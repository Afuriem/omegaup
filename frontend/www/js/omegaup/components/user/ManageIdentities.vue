<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h2 class="panel-title">{{ T.profileManageIdentities }}</h2>
    </div>
    <div class="panel-body">
      <form class="form"
            v-on:submit.prevent="onAddIdentity">
        <div class="form-group">
          <label>{{ T.wordsIdentity }}</label> <span aria-hidden="true"
               class="glyphicon glyphicon-info-sign"
               data-placement="top"
               data-toggle="tooltip"
               v-bind:title="T.profileAddIdentitiesTooltip"></span> <input autocomplete="off"
               class="form-control"
               size="20"
               type="text"
               v-model="username">
        </div>
        <div class="form-group">
          <label>{{ T.loginPassword }}</label> <input autocomplete="off"
               class="form-control"
               size="20"
               type="password"
               v-model="password">
        </div>
        <div class="form-group pull-right">
          <button class="btn btn-primary"
               type="submit">{{ T.wordsAddIdentity }}</button>
        </div>
      </form>
      <div v-if="identities.length == 0">
        <div class="empty-category">
          {{ T.profileIdentitiesEmpty }}
        </div>
      </div>
      <table class="table table-striped table-over"
             v-else="">
        <thead>
          <tr>
            <th>{{ T.wordsIdentity }}</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="identity in identities">
            <td>{{ identity.username }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import UI from '../../ui.js';
import {T} from '../../omegaup.js';

export default {
  props: {
    identities: Array,
  },
  data: function() {
    return {
      T: T,
      username: '',
      password: '',
    };
  },
  methods: {
    onAddIdentity: function() {
      this.$emit('add-identity', this.username, this.password);
    },
  },
};
</script>

<style>
th.align-right {
  text-align: right;
}
</style>
