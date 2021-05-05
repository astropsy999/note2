<template>
  <div class="notes">
    <div
      class="note"
      :class="{ full: !grid }"
      v-for="(note, index) in notes"
      :key="index"
    >
      <div class="note-header" :class="{ full: !grid }">
        <p>{{ note.title }}</p>
        <p class="note-close" @click="removeNote(index)">x</p>
      </div>
      <div class="note-body">
        <p>{{ note.descr }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true,
    },
    grid: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      this.notes.splice(index, 1)
    },
  },
}
</script>

<style lang="scss">
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: white;
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.16);
  &:hover {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.36);
    transform: translate (0, -6px);
    transition-delay: 0s !important;
  }
  &.full {
    width: 100%;
  }
}
.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  h1 {
    font-size: 22px;
  }
  p {
    color: #402caf;
    font-size: 22px;
  }
  svg {
    margin-right: 12px;
    color: #999999;
    cursor: pointer;
    &.active {
      color: #402caf;
    }
    &:last-child {
      margin-right: 0;
    }
  }
}
.note-body {
  p {
    margin: 20px 0;
  }
  span {
    font-size: 14px;
    color: #999;
  }
}
.note-close {
  cursor: pointer;
}
</style>
