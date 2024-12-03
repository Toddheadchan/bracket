<template>
  <div class="bracket-node">
    <div class="bracket-block" v-if="type != 'blank'">
      <div :class="focusWinCheckedClass('father-vertical')">
        <div class="top" :class="{'normal': type == 'bottom'}"/>
        <div class="bottom" :class="{'normal': type == 'top'}"/>
      </div>
      <div :class="focusWinCheckedClass('out-line')" v-if="type != 'final'"/>
      <div class="content-block">
        <div class="serial">set {{bracket.serialv}}</div>
        <div :class="nodeClass('1')">
          <div class="slot" :class="{'loser-slot' : bracket.winnerId && bracket.winnerId != bracket.player1Id}">
            <div class="name"
              :class="{'me': checkPlayer1, 'empty': !bracket.player1Id}">{{bracket.player1Nickname || '-'}}</div>
            <div class="score"
              :class="{'me': checkPlayer1, 'empty': !bracket.player1Id}">{{bracket.player1Score}}</div>
          </div>
          <div class="slot" :class="{'loser-slot' : bracket.winnerId && bracket.winnerId != bracket.player2Id}">
            <div class="name"
              :class="{'me': checkPlayer2, 'empty': !bracket.player2Id}">{{bracket.player2Nickname || '-'}}</div>
            <div class="score"
              :class="{'me': checkPlayer2, 'empty': !bracket.player2Id}">{{bracket.player2Score}}</div>
          </div>
        </div>
      </div>
      <div :class="focusCheckedClass('out-line')" v-if="bracket.children && bracket.children.length"/>
      <div class="children-block" v-if="bracket.children">
        <div class="children">
          <!-- 只有一个子节点 -->
          <template v-if="bracket.children.length == 1">
            <Bracket :bracket="bracket.children[0]" type="single"/>
          </template>
          <!-- 两个子节点 -->
          <template v-if="bracket.children.length == 2">
            <Bracket :bracket="bracket.children[0]" type="top"/>
            <Bracket :bracket="bracket.children[1]" type="bottom"/>
          </template>
        </div>
      </div>
    </div>
    <div class="blank-node" v-if="type == 'blank'" />
  </div>
</template>

<script>
export default {
  name: 'Bracket',
  props: {
    bracket: {
      type: Object
    },
    type: {
      type: String,
      default: 'final'
    }
  },
  data () {
    return {
      myId: ''
    }
  },
  mounted () {
    this.myId = '00001'
  },
  methods: {
    focusCheckedClass: function (str) {
      if (this.myId == this.bracket.player1Id || this.myId == this.bracket.player2Id) {
        return 'focus ' + str
      }
      return str
    },
    focusWinCheckedClass: function (str) {
      if (this.myId == this.bracket.winnerId) {
        return 'focus ' + str
      }
      return str
    },
    nodeClass: function (s) {
      let ret = 'node'
      if (this.myId == this.bracket.player1Id || this.myId == this.bracket.player2Id) {
        ret = 'focus ' + ret
      }
      if (this.bracket.focus) {
        ret = 'notice ' + ret
      }
      return ret
    }
  },
  computed: {
    checkPlayer1: function () {
      if (this.myId == this.bracket.player1Id) {
        return true
      }
      return false
    },
    checkPlayer2: function () {
      if (this.myId == this.bracket.player2Id) {
        return true
      }
      return false
    }
  }
}
</script>

<style lang="less" scoped>
.bracket-block {
  display: flex;
  flex-direction: row-reverse;
  align-items: center;
  position: relative;
  padding: 10px 0;
  .father-vertical {
    flex-shrink: 0;
    position: absolute;
    width: 1px;
    height: 100%;
    .top {
      height: 50%;
    }
    .bottom {
      height: 50%;
    }
    .normal {
      background-color: #A0A0A0;
    }
    &.focus {
      .normal {
        background-color: #FF3B3B;
      }
    }
  }
  .out-line {
    height: 1px;
    width: 20px;
    background-color: #A0A0A0;
    flex-shrink: 0;
    &.focus {
      background-color: #FF3B3B;
    }
  }
  .content-block {
    .serial {
      padding-left: 12px;
    }
    .node {
      border: 1px solid #A0A0A0;
      padding: 5px;
      border-radius: 10px;
      flex-shrink: 0;
      &.player1-loser {
        &::after {
          content: '';
          width: 100%;
          height: 50%;
          background-color: #A0A0A0;
        }
      }
      .slot {
        display: flex;
        padding-left: 6px;
        .name {
          width: 150px;
          &.me {
            color: #FF3B3B;
            font-weight: 550;
          }
          &.empty {
            color: #808080;
          }
        }
        .score {
          width: 20px;
          &.me {
            color: #FF3B3B;
            font-weight: 550;
          }
        }
        &:nth-child(n+2) {
          margin-top: 3px;
        }
      }
      &.focus {
        border: 1px solid #FF3B3B;
      }
      &.notice {
        background: repeating-linear-gradient(-68.2deg, #2F2F2F, #2F2F2F 10px, #484848 0, #484848 20px);
      }
    }
  }
}
.blank-node {
  height: 77px;
  width: 208px;
}
</style>
