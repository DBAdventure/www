<template>
  <div
    v-if="Object.keys(data).length > 0"
    class="details"
  >
    <p>
      <strong>{{ $t('bonus.name') }}</strong>
    </p>

    <ul class="stats">
      <li
        v-for="(value, key) in data"
        :key="key"
        v-html="$t(`objects.details.${key}`, {value: getValue(key, value)})"
      />
    </ul>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      data: {
        type: [Object, Array],
        required: true,
      },
    },
    methods: {
      getValue(key, value) {
        if (key === 'teleport') {
          return this.$t(`game.teleport.where.${value}`);
        }

        return value;
      },
    },
  };
</script>
