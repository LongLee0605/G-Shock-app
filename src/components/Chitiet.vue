<template>
  <Page>
    <ActionBar :title="item.title">
      <NavigationButton
        text="Go back"
        android.systemIcon="ic_menu_back"
        @tap="$navigateBack"
      />
      <ActionItem :text="'ID: ' + item.id" android.position="actionBar" />
    </ActionBar>
    <ScrollView>
      <StackLayout orientation="vertical" backgroundColor="#ffffff">
        <GridLayout
          columns="*, *"
          rows="*, *, *"
          borderBottomColor="black"
          borderBottomWidth="1"
        >
          <Image :src="item.imageUrl" width="100%" />
          <Label
            col="1"
            row="0"
            :text="'Giới thiệu sản phẩm: ' + item.description"
            class="justify"
            textWrap="true"
            fontSize="14"
          />
          <Label
            col="1"
            row="0"
            :text="'Giá: ' + item.price + ' VNĐ'"
            class="justify"
            textWrap="true"
            fontSize="16"
            color="red"
            marginTop="133"
          />

          <GridLayout
            paddingRight="20"
            verticalAlignment="center"
            col="1"
            row="0"
            columns="*, *, *"
            rows="*, *, *"
          >
            <Button
              col="0"
              row="2"
              fontSize="10"
              width="50"
              height="35"
              text="Mua"
              backgroundColor="#009933"
              color="#e0ebeb"
              @tap="toGoCart(item.amount++)"
              marginTop="150"
            />
            <Button
              col="2"
              row="2"
              fontSize="10"
              text="Thêm"
              width="70"
              height="35"
              backgroundColor=""
              @tap="item.amount++"
              marginTop="150"
            />
          </GridLayout>
        </GridLayout>
        <Tabs height="300px">
          <TabStrip>
            <TabStripItem>
              <Label text="Thông tin chi tiết"></Label>
            </TabStripItem>
            <TabStripItem>
              <Label text="Thông tin liên quan"></Label>
            </TabStripItem>
          </TabStrip>
          <TabContentItem>
             <GridLayout>
              <Label
                text="Cái này cũng tính là 1 tính năng rồi"
                class="justify"
                textWrap="true"
                fontSize="16"
                color="black"
              />
            </GridLayout>
            <GridLayout>
              <Label
                :text="item.info"
                class="justify"
                textWrap="true"
                fontSize="16"
                color="black"
              />
            </GridLayout>
          </TabContentItem>
          <TabContentItem>
            <GridLayout>
              <Image :src="item.imginfo" width="100%"/>
            </GridLayout>
            <GridLayout>
              <Label
                text="Làm cho vui chứ chỗ này em hổng biết nên ghi gì nên để vầy đi nào có ý tưởng thì em làm tiếp :V"
                class="justify"
                textWrap="true"
                fontSize="16"
                color="black"
              />
            </GridLayout>
          </TabContentItem>
        </Tabs>
      </StackLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Cart from "./Cart";
export default {
  props: ["item"],
  data() {
    return {
      itemSelected: 0,
      priceAll: 0,
    };
  },
  methods: {
    toGoCart() {
      this.$navigateTo(Cart, {
        props: { carts: this.carts },
        animated: true,
        transition: {
          name: "slideLeft",
          duration: 250,
          curve: "easeIn",
        },
      });
    },
  },
  watch: {
    item: {
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
}

.image-title {
  width: 150px;
}

.title {
  text-align: center;
}
.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}

.justify {
  text-align: justify;
}
</style>
