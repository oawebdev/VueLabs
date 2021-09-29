<template>
  <v-list
    subheader
    flat
    class="pa-6"
  >
    <v-text-field
      v-model="newItemTitle"
      label="Додати елемент"
      append-icon="mdi-cart-plus"
      clearable
      @click:append="addNewItem()"
      @keyup.enter="addNewItem()"
    ></v-text-field>
    <div v-for="item in shoppingList"
         :key="item.id">
      <v-list-item
        @click="doneBought(item.id)"
        :class="{ 'blue lighten-5' : item.bought }"
      >
        <template>
          <v-list-item-action>
            <v-checkbox
              :input-value="item.bought"
              color="primary"
            ></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title
              :class="{ 'text-decoration-line-through' : item.bought }"
            >{{ item.title }}</v-list-item-title>
          </v-list-item-content>
          <v-list-item-action>
            <v-btn icon @click.stop="deleteItem(item.id)">
              <v-icon color="grey lighten-1">mdi-delete</v-icon>
            </v-btn>
          </v-list-item-action>
        </template>

      </v-list-item>
    <v-divider></v-divider>
    </div>
  </v-list>
</template>

<script>

export default {
  name: 'List',

  data: () => ({
    shoppingList: [
      {
        id: 1, title: 'Овочі', bought: false
      },
      {
        id: 2, title: 'Фрукти', bought: false
      },
      {
        id: 3, title: 'Напої', bought: false
      }
    ],
    // Змінна для створення нових елементів списка
    newItemTitle: ''
  }),

  components: {

  },
  methods: {
    /**
     * Відмічаємо елемент як куплений.
     */
    doneBought: function (id) {
      // в списку шукаємо потрібний запис
      const item = this.shoppingList.filter(item => item.id === id)[0]
      // Змінюємо статус покупки
      item.bought = !item.bought
    },
    /**
     * Видаляємо елемент зі списка
     */
    deleteItem: function (id) {
      // перебираемо всі елементи в списку і дивимось,
      // щоб його id не збігався з тим, який треба видалити.
      this.shoppingList = this.shoppingList.filter(item => item.id !== id)
    },
    /**
     * Додаємо новий елемент
     */
    addNewItem: function () {
      // Створюємо новий елемент з правильною структурою
      const newItem = {
        id: Date.now(),
        title: this.newItemTitle,
        bought: false
      }
      // додаємо створений елемент до існуючого списка
      this.shoppingList.push(newItem)
      // очищуємо поле вводу
      this.newItemTitle = ''
    }
  }
}
</script>
