<template>
  <div class="home" :style="{'width': bracketWidth}">
    <Bracket :bracket="bracket" />
  </div>
</template>

<script>
import Bracket from '@/components/Bracket'
export default {
  name: 'Home',
  components: { Bracket },
  data () {
    return {
      bracket: {
        "id": "10007",
        "serial": 8,
        "player1Id": "00001",
        "player1Nickname": "Ke",
        "player2Id": "00002",
        "player2Nickname": "ASH",
        "winnerId": "00001",
        "focus": 0,
        "room": null,
        "round": 4,
        "winnerTo": 0,
        "loserTo": 0,
        "roundMark": "gf",
        "losingResult": 2,
        "status": "finish",
        "player1Score": 3,
        "player2Score": 1,
        "roundText": "总决赛",
        "serialv": "N",
        "children": [{
          "id": "10000",
          "serial": 1,
          "player1Id": "00002",
          "player1Nickname": "ASH",
          "player2Id": "00001",
          "player2Nickname": "Ke",
          "winnerId": "00001",
          "focus": 0,
          "room": null,
          "round": 3,
          "winnerTo": 8,
          "loserTo": 9,
          "roundMark": "wf",
          "losingResult": 2,
          "status": "finish",
          "player1Score": 2,
          "player2Score": 3,
          "roundText": "胜者组 决赛",
          "serialv": "G",
          "children": [{
              "id": "10001",
              "serial": 3,
              "player1Id": "00002",
              "player1Nickname": "ASH",
              "player2Id": "00003",
              "player2Nickname": "ABAN",
              "winnerId": "00002",
              "focus": 0,
              "room": null,
              "round": 2,
              "winnerTo": 1,
              "loserTo": 12,
              "roundMark": "wsf",
              "losingResult": 3,
              "status": "finish",
              "player1Score": 3,
              "player2Score": 2,
              "roundText": "胜者组 半决赛",
              "serialv": "E",
              "children": [{
                  "id": "10002",
                  "serial": 7,
                  "player1Id": "00002",
                  "player1Nickname": "ASH",
                  "player2Id": "00004",
                  "player2Nickname": "BestNaisi",
                  "winnerId": "00002",
                  "focus": 0,
                  "room": null,
                  "round": 1,
                  "winnerTo": 3,
                  "loserTo": 14,
                  "roundMark": "wr",
                  "losingResult": 5,
                  "status": "finish",
                  "player1Score": 3,
                  "player2Score": 0,
                  "children": [],
                  "roundText": "胜者组 第一轮",
                  "serialv": "A"
                },
                {
                  "id": "10003",
                  "serial": 4,
                  "player1Id": "00005",
                  "player1Nickname": "Cheng",
                  "player2Id": "00003",
                  "player2Nickname": "ABAN",
                  "winnerId": "00003",
                  "focus": 0,
                  "room": null,
                  "round": 1,
                  "winnerTo": 3,
                  "loserTo": 14,
                  "roundMark": "wr",
                  "losingResult": 5,
                  "status": "finish",
                  "player1Score": "",
                  "player2Score": "W",
                  "children": [],
                  "roundText": "胜者组 第一轮",
                  "serialv": "B"
                }
              ]

            },
            {
              "id": "10004",
              "serial": 2,
              "player1Id": "00001",
              "player1Nickname": "Ke",
              "player2Id": "00006",
              "player2Nickname": "Fenghao",
              "winnerId": "00001",
              "focus": 0,
              "room": null,
              "round": 2,
              "winnerTo": 1,
              "loserTo": 11,
              "roundMark": "wsf",
              "losingResult": 3,
              "status": "finish",
              "player1Score": 3,
              "player2Score": 2,
              "roundText": "胜者组 半决赛",
              "serialv": "F",
              "children": [{
                  "id": "10005",
                  "serial": 6,
                  "player1Id": "00001",
                  "player1Nickname": "Ke",
                  "player2Id": "00007",
                  "player2Nickname": "Ribrow",
                  "winnerId": "00001",
                  "focus": 0,
                  "room": null,
                  "round": 1,
                  "winnerTo": 2,
                  "loserTo": 13,
                  "roundMark": "wr",
                  "losingResult": 5,
                  "status": "finish",
                  "player1Score": 3,
                  "player2Score": 0,
                  "children": [],
                  "roundText": "胜者组 第一轮",
                  "serialv": "C"
                },
                {
                  "id": "10006",
                  "serial": 5,
                  "player1Id": "00006",
                  "player1Nickname": "Fenghao",
                  "player2Id": "00008",
                  "player2Nickname": "LIMa",
                  "winnerId": "00006",
                  "focus": 0,
                  "room": null,
                  "round": 1,
                  "winnerTo": 2,
                  "loserTo": 13,
                  "roundMark": "wr",
                  "losingResult": 5,
                  "status": "finish",
                  "player1Score": 3,
                  "player2Score": 0,
                  "children": [],
                  "roundText": "胜者组 第一轮",
                  "serialv": "D"
                }
              ],
            }
          ]

        }]
      }
    }
  },
  computed: {
    bracketWidth: {
      get: function () {
        return `${this.bracket.round * 220}px`
      }
    }
  }
}
</script>

<style lang="less" scoped>
.home {
  text-align: left;
  margin: 0 auto;
}
</style>
