<template>
  <v-row justify="space-around" class="width-100pc">
    <v-col>
      <v-sheet tile elevation="2" class="width-100pc">
        <v-chip-group
          mandatory
          class="ml-1 bar-chip-group"
          active-class="chip-active"
          v-model="activeIndex"
        >
          <v-chip
            v-for="(item, index) in visitedItems"
            :key="index"
            :close="item.deletable"
            class="bar-chip"
            label
            small
            outlined
            close-icon="mdi-close"
            @click="active(item, index)"
            @click.right="showOperationMenu($event, item)"
            @click:close="close(item)"
          >
            {{ item.name }}
          </v-chip>
          <v-menu
            :position-x="x"
            :position-y="y"
            absolute
            offset-y
            v-model="showOperation"
          >
            <v-list dense>
              <v-list-item
                v-for="(operationItem, operationIndex) in operation"
                :key="operationIndex"
                @click="opertaionClick(operationItem)"
              >
                <v-list-item-title>
                  {{ operationItem.text }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </v-chip-group>
      </v-sheet>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "VisitedBar",

  data: () => ({
    activeIndex: 0,
    defaultItems: [],
    showOperation: false,
    showOperationItem: null,
    x: 0,
    y: 0,
    operation: [
      {
        text: "Cerrar esta pagina",
        type: 1,
      },
      {
        text: "Cerrar otras páginas",
        type: 2,
      },
      {
        text: "Cerrar todas las paginas",
        type: 3,
      },
    ]
  }),
  computed: {
    visitedItems() {
      return this.$store.state.visitedItems;
    },
  },
  watch: {
    $route() {
      this.addItem();
    },
  },
  methods: {
    active(item, index) {
      
      this.activeIndex = index;
      if (item.path === this.$route.path) {
        return;
      }
      this.$router.push({ path: item.path });
    },
    addItem() {
      const route = this.$route;
      
      const currentRouteIndex = this.visitedItems.findIndex(
        (i) => i.path === route.path
      );
      if (currentRouteIndex !== -1) {
        this.refresh(this.visitedItems[currentRouteIndex], currentRouteIndex);
        return;
      }

      const originalLength = this.visitedItems.length;
      const visitedItem = {
        name: route.meta.title, //|| route.name,
        path: route.path,
        deletable: route.path !== "admin/"
      };
      this.$store.dispatch("addItem", visitedItem);
      this.refresh(visitedItem, originalLength);
    },
    close(item) {
      const preIndex = this.visitedItems.indexOf(item) - 1;
      this.$store.dispatch("removeItem", item);
      this.active(this.visitedItems[preIndex], preIndex)
    },
    refresh(item, index) {
      this.$nextTick(() => {
        this.active(item, index);
      })
    },
    showOperationMenu(e, item) {
      e.preventDefault();
      if (!item.deletable) {
        return;
      }
      this.showOperation = false;
      this.showOperationItem = item;
      this.x = e.clientX;
      this.y = e.clientY;
      this.$nextTick(() => {
        this.showOperation = true;
      })
    },
    opertaionClick(operation) {
      const item = this.showOperationItem;
      switch (operation.type) {
        case 1:
          this.close(item);
          break;
        case 2:
          var items2 = this.visitedItems.filter(
            (element) => element === item || !element.deletable
          );
          this.$store.dispatch("replaceItems", items2);
          this.active(item, items2.indexOf(item));
          break;
        case 3:
          var items3 = this.visitedItems.filter(
            (element) => !element.deletable
          );
          this.$store.dispatch("replaceItems", items3);
          this.active(items3[0], 0);
          break;
        default:
      }
    },
  },
  mounted() {
    this.addItem();
  },
};
</script>

<style scoped>
.bar-sheet {
  width: 100%;
}
.chip-group {
  max-width: calc(100% - 0);
  overflow-x: auto;
}
.chip-active {
  /*border-bottom: #85b71b solid 3px !important;*/
  border-bottom: #2a68c9 solid 2px !important;
}

.bar-chip {
  border-radius: 0 !important;
  height: 26px !important;
  margin-top: 2px !important;
  margin-bottom: 2px !important;
}

.bar-chip:hover {
  border-bottom: #2a68c9 solid 2px !important;
}

.operation-text {
  font-size: 12px;
  line-height: 18px;
  height: 18px;
}
</style>
