<template>
    <Page class="page" backgroundSpanUnderStatusBar="true">
        <ActionBar title="Đồng hồ G-Shock Nam giá rẻ">
            <NavigationButton
                text="Go back"
                android.systemIcon="ic_menu_back"
                @tap="$navigateBack"
                />
            <StackLayout  orientation="horizontal">
                <label text="Đồng hồ G-Shock Nam giá rẻ" width="70%" fontSize="20" fontWeight="bold" verticalAlignment="center"></label>
                <label :text="'(Cart: ' + itemSelected + ')'" fontSize="20"></label>
            </StackLayout>
        </ActionBar>
        <!-- Search -->
        <StackLayout backgroundColor="ffffff">
            <SearchBar v-model="searchQuery" 
                @textChange="onTextChanged"
                @submit="onSubmit" />
            <ScrollView>
                <StackLayout orientation="vertical" backgroundColor="#ffffff">
                    <GridLayout
                        columns="100, *, auto"
                        rows="*,*"
                        borderBottomColor="black"
                        borderBottomWidth="1"
                        v-for="(phone, i) in filteredPhones"
                        :key="i"
                        >
                        <Image
                            col="0"
                            :src="phone.imageUrl"
                            marginRight="10"
                            marginLeft="10"
                            />
                        <StackLayout
                            col="1"
                            orientation="vertical"
                            paddingTop="10"
                            paddingBottom="10"
                            >
                            <Label :text="phone.title" color="#b30000" fontWeight="bold" />
                            <Label :text="'(' + phone.price + ' VNĐ)'" />
                                <StackLayout orientation="horizontal" marginTop="10">
                                    <Image
                                        width="20"
                                        height="20"
                                        marginRight="10"
                                        src="~/assets/images/icon.png"
                                        />
                            <Label :text="phone.amount" />
                            </StackLayout>
                        </StackLayout>
                        <GridLayout
                            paddingRight="20"
                            verticalAlignment="center"
                            col="3"
                            columns="*, *, *"
                            rows="*, *, *"
                            >
                        <Button
                            col="2"
                            row="0"
                            fontSize="10"
                            width="50"
                            height="35"
                            text="Mua"
                            backgroundColor="#009933"
                            color="#e0ebeb"
                            verticalAlignment="center"
                            @tap="toGoCart(phone.amount++)"
                            />
                        <Button 
                            col="2"
                            row="2"
                            fontSize="10"
                            text="Thêm"
                            width="70"
                            height="35"
                            backgroundColor="#ffffff"
                            @tap="phone.amount++"
                            />
                        </GridLayout>
                    </GridLayout>
                    <GridLayout columns="*" rows="*, *" />
                        <GridLayout columns="*" rows="*, *, *, *" horizontalAlignment="center">
                            <StackLayout horizontalAlignment="center">
                                <Label  class="font-weight-bold"
                                    fontSize="17" color="#000000"
                                    text="Viết bởi Đăng Long lớp CD18LW3" horizontalAlignment="center"
                                    verticalAlignment="center"></Label>     
                                <label class="font-weight-blod"
                                    fontSize="13" color="black"
                                    text="© 2021 - Bản quyền thuộc về Đăng Long vui lòng đừng coppy :V" horizontalAlignment="center"
                                    verticalAlignment="center"></label>     
                            </StackLayout>
                        </GridLayout>
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </Page>
</template>
<script>
    import * as app from "tns-core-modules/application";
    import * as platform from "tns-core-modules/platform";
    import * as color from "tns-core-modules/color";
    // import { isIOS, isAndroid } from 'tns-core-modules/platform';
    import Cart from './Cart';
    import App from './App';
    export default {
    	
    	// created() {
    	// 	console.log('is IOS platform: ' + isIOS)
    	// 	console.log('is Android platform: ' + isAndroid)
    	// },
    	data() {
    		return {
    			itemSelected: 0,
          priceAll: 0,
          searchedText: "",
          searchQuery: "",
    		}
    	},
    	props: ["phones"],
    	
      	methods: {
          pageLoaded() {
            if (app.android && platform.device.sdkVersion >= "21") {
                const window = app.android.foregroundActivity.getWindow();
                window.setStatusBarColor(new color.Color("#ffffff").android);
            }
          },
          onTextChanged(event) {
            console.log("text changed to", this.searchQuery);
            this.searchedText = this.searchQuery;
          },
          onSubmit() {
            console.log("submitted text is", this.searchQuery);
            this.searchedText = this.searchQuery;
          },
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
        computed: {
          filteredPhones: function () {
    					var move_array = this.phones,
    							searchedText = this.searchedText;
    
    					if(!searchedText){
    							return move_array;
    					}
    
    					searchedText = searchedText.trim().toLowerCase();
    
    					move_array = move_array.filter(function(phone){
    							if(phone.title.toLowerCase().indexOf(searchedText) !== -1){
    									return phone;
    							}
    					})
    
    					// Return an array with the filtered data.
    					return move_array;;
    			}
        },
      	watch: {
        
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
            this.carts = newApp.filter(f => f.amount > 0);
            console.log(this.carts);
          },
        },
      },
    };
</script>
<style scoped>
    ActionBar {
    background-color: #000000;
    color: white;
    }
    .title{
      text-align: center;
    }
</style>