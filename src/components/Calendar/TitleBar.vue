
<template>
  <div class="calendar-pro__title">
    <div class="calendar-pro__title-info">
      <span class="calendar-pro__year">
        <el-select v-model="defaultYear" @change="renderYear" placeholder="请选择">
          <el-option
            v-for="item in yearOptions"
            :key="item"
            :label="`${item}年`"
            :value="item">
          </el-option>
        </el-select>
      </span>
      <span class="calendar-pro__month">
        <el-select v-model="defaultMonth" @change="renderMonth" placeholder="请选择">
          <el-option
            v-for="item in 12"
            :key="item"
            :label="`${item}月`"
            :value="item">
          </el-option>
        </el-select>
      </span>
    </div>
    <div v-if="showControlBtn" class="calendar-pro__tool">
      <!-- <button @click="turn(-12)">上一年</button> -->
      <button class="hk-btn-gray" @click="turn(-1)">上一月</button>
      <button class="hk-btn-gray" :class="{'today': today}" @click="turnNow()">今日</button>
      <button class="hk-btn-gray" @click="turn(1)">下一月</button>
      <!-- <button @click="turn(12)">下一年</button> -->
    </div>
  </div>
</template>

<script type="text/babel">
  export default {
    name: "TitleBar",
    props: {
      year: [Number,String],
      month: [Number,String],
      // 是否显示控制按钮
      showControlBtn: {
        type: Boolean,
        default: true
      },
    },
    data() {
      return {}
    },
    computed: {
      defaultYear: {
        get() {
          return this.year
        },
        set(val) {
          return this.$emit('update:year', val)
        }
      },
      defaultMonth: {
        get() {
          return this.month
        },
        set(val) {
          return this.$emit('update:month', val)
        }
      },
      today() {
        let today = new Date()
        return this.defaultYear === today.getFullYear() && this.defaultMonth === today.getMonth() + 1
      },
      yearOptions() {
        let arr = []
        for(let i = 1900; i < 2100; i++) {
          arr.push(i)
        }
        return arr
      },
    },
    methods: {
      turn(val) {
        this.$emit('turn', val)
      },
      turnNow() {
        this.$emit('turnNow')
      },
      renderYear(year) {
        this.$emit('render', year, this.defaultMonth)
      },
      renderMonth(month) {
        this.$emit('render', this.defaultYear, month)
      }
    },
  }
</script>
