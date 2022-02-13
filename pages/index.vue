<!--
    ledger-app is a simple web app that helps you manage your personal financial situation.
    Copyright (C) 2022  Petru Szemereczki

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
-->
<template>
  <div class="ledger">
    <b-table
      striped
      hover
      :fields="fields"
      :items="mock"
    >
      <template #custom-foot>
        <b-tr>
          <b-th>
            <b-input-group class="mb-3">
              <b-form-input
                v-model="ledger.date"
                type="text"
                placeholder="YYYY-MM-DD"
                autocomplete="off"
              />
              <b-input-group-append>
                <b-form-datepicker
                  v-model="ledger.date"
                  button-only
                  right
                  locale="en-US"
                />
              </b-input-group-append>
            </b-input-group>
          </b-th>
          <b-th>
            <b-form-input
              v-model="ledger.details"
              type="text"
              placeholder="Choose a category..."
            />
          </b-th>
          <b-th>
            <b-form-select
              v-model="ledger.happened"
              :options="happened"
            />
          </b-th>
          <b-th>
            <b-form-input
              v-model="ledger.decrease"
              type="number"
              placeholder="0.00"
            />
          </b-th>
          <b-th>
            <b-form-input
              v-model="ledger.increase"
              type="number"
              placeholder="0.00"
            />
          </b-th>
          <b-th>
            <b-btn
              variant="primary"
              @click="save"
            >
              <fa icon="save" />
            </b-btn>
          </b-th>
        </b-tr>
        <b-tr class="bg-secondary">
          <b-th colspan="5" class="text-white text-right">
            Total:
          </b-th>
          <b-th class="text-white">
            0.00
          </b-th>
        </b-tr>
      </template>
    </b-table>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data (): any {
    return {
      mock: [],
      ledger: {
        date: '2022-02-10',
        details: null,
        happened: false,
        decrease: 0.00,
        increase: 0.00
      },
      fields: [
        { key: 'date' },
        { key: 'details' },
        { key: 'happened' },
        { key: 'decrease' },
        { key: 'increase' },
        { key: 'balance' }
      ],
      happened: [
        {
          value: null,
          text: 'Choose...',
          disabled: true,
          selected: true
        },
        {
          value: true,
          text: 'Y'
        },
        {
          value: false,
          text: 'N'
        }
      ]
    }
  },
  computed: {
    items (): any[] {
      return []
    }
  },
  watch: {
    'ledger.decrease' () {
      this.ledger.increase = 0
    },
    'ledger.increase' () {
      this.ledger.decrease = 0
    }
  },
  methods: {
    save (): void {
      const increase = parseFloat(this.ledger.increase)
      const decrease = parseFloat(this.ledger.decrease)

      let balance = 0
      if (this.mock.length > 0) {
        balance = parseFloat(this.mock[this.mock.length - 1].balance)
      }

      balance = balance + (increase - decrease)

      const _ledger = {
        ...this.ledger,
        decrease: decrease > 0 ? decrease.toFixed(2) : '',
        increase: increase > 0 ? increase.toFixed(2) : '',
        balance: balance.toFixed(2)
      }

      this.mock.push(_ledger)

      this.ledger = {
        date: '2022-02-10',
        details: null,
        happened: false,
        decrease: 0.00,
        increase: 0.00
      }
    }
  }
})
</script>

<style lang="css">
.ledger {
  padding: 2rem;
}
</style>
