<template>
  <Page>
    <ActionBar title="Đơn hàng">
            <NavigationButton
                text="Go back"
                android.systemIcon="ic_menu_back"
                @tap="$navigateBack"
                />
      <ActionItem text="Home" android.position="actionBar" @tap="goApp()" />
    </ActionBar>
    <ScrollView>
      <StackLayout
        orientation="vertical"
        paddingLeft="30"
        paddingRight="30"
        backgroundColor="#ffffff"
      >
        <GridLayout
          columns="100, 120, 0, auto"
          rows="*"
          marginTop="10"
          borderBottomColor="black"
          borderBottomWidth="1"
          v-for="(cms, i) in carts"
          :key="i"
        >
          <Image col="0" :src="cms.imageUrl" marginRight="10" marginLeft="10" />
          <StackLayout col="1">
            <Label :text="cms.title" color="#b30000" fontWeight="bold" />
            <Label
              :text="cms.price + ' VNĐ'"
              color="red"
              fontWeight="bold"
              marginTop="50"
            />
          </StackLayout>
          <Label
            col="3"
            :text="'Amount: ' + cms.amount"
            verticalAlignment="center"
            marginLeft="7"
            marginRight="10"
            marginBottom="50"
          />
          <StackLayout paddingRight="20" verticalAlignment="center" col="3">
            <Label
              col="2"
              fontSize="15"
              color="red"
              :text="cms.amount * cms.price + ' VNĐ'"
              marginLeft="7"
              marginRight="10"
              marginTop="50"
              verticalAlignment="center"
            />
          </StackLayout>
          <GridLayout
            paddingRight="20"
            verticalAlignment="center"
            col="4"
            columns="*, *, *"
            rows="*, *, *"
          >
            <Button
              col="0"
              row="0"
              fontSize="13"
              width="35"
              height="35"
              text="-"
              backgroundColor="#002e4a"
              color="#ffffff"
              verticalAlignment="center"
              @tap="cms.amount--"
            />
            <Button
              col="2"
              row="0"
              fontSize="13"
              text="+"
              width="35"
              height="35"
              backgroundColor="#002e4a"
              color="#ffffff"
              @tap="cms.amount++"
            />
          </GridLayout>
        </GridLayout>
        <StackLayout>
          <Label
            color="red"
            fontSize="24"
            marginTop="20"
            :text="'Tổng : ' + totalPrice + ' VNĐ'"
          ></Label>
          <Button
            color="#ffffff"
            backgroundColor="#002e4a"
            text="Đặt hàng"
            fontSize="20"
            marginTop="10"
          />
        </StackLayout>
        <GridLayout columns="*" rows="*, *" />
        <GridLayout columns="*" rows="*, *, *, *" horizontalAlignment="center">
          <StackLayout horizontalAlignment="center">
            <Label
              class="font-weight-bold"
              fontSize="17"
              color="#000000"
              text="Viết bởi Đăng Long lớp CD18LW3"
              horizontalAlignment="center"
              verticalAlignment="center"
            ></Label>
            <label
              class="font-weight-blod"
              fontSize="13"
              color="black"
              text="© 2021 - Bản quyền thuộc về Đăng Long vui lòng đừng coppy :V"
              horizontalAlignment="center"
              verticalAlignment="center"
            ></label>
          </StackLayout>
        </GridLayout>
      </StackLayout>
    </ScrollView>
  </Page>
</template>
<script>
import App from "./App";
export default {
  data() {
    return {};
  },
  props: ["carts"],
  computed: {
    totalPrice: function() {
      return this.carts.reduce((a, o) => o.amount * o.price + a, 0);
    },
  },
  watch: {
    filteredLaptops: {
      deep: true,
      handler(newApp, old) {
        this.priceAll = newApp.reduce((a, f) => {
          return f.price * f.amount + a;
        }, 1);
        this.itemSelected = newApp.filter((f) => {
          if (f.amount > 0) {
            return f;
          }
        }).length;
        this.carts = newApp.filter((f) => f.amount > 0);
        console.log(this.carts);
      },
    },
    filteredPcgamings: {
      deep: true,
      handler(newApp, old) {
        this.priceAll = newApp.reduce((a, item) => {
          return item.price * item.amount + a;
        }, 0);
        this.itemSelected = newApp.filter((item) => {
          if (item.amount > 0) {
            return item;
          }
        }).length;
        this.carts = newApp.filter((item) => item.amount > 0);
        console.log(this.carts);
      },
    },
    filteredPhones: {
      deep: true,
      handler(newApp, old) {
        this.priceAll = newApp.reduce((a, f) => {
          return f.price * f.amount + a;
        }, 0);
        this.itemSelected = newApp.filter((f) => {
          if (f.amount > 0) {
            return f;
          }
        }).length;
        this.carts = newApp.filter((f) => f.amount > 0);
        console.log(this.carts);
      },
    },
  },
};
</script>
<style scoped>
ActionBar {
  background-color: black;
  color: white;
  font-size: 22;
  font-weight: bold;
}
.title {
  text-align: center;
}
</style>
