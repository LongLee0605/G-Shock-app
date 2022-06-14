<template>
    <Page>
        <ActionBar title="Trang Chủ" verticalAlignment="center">
            <!-- <ActionItem 
                :text="'(Cart: ' + itemSelected + ')'" android.position="actionBar" @tap="toGoCart()"/> -->
            <ActionItem 
                text="Đăng Nhập" android.position="popup" @tap="toGoLogin()" />
            <ActionItem 
                text="Đăng Ký" android.position="popup"  @tap="toGoLogin()"/>
        </ActionBar>
        <GridLayout orientation="vertical" width="100%" height="100%" columns="*"
            rows="*,auto">
            <StackLayout col="0" row="0" backgroundColor="#ffffff">
                <!-- bìa -->
                <ScrollView orientation="vertical">
                    <StackLayout>
                        <Image height="100%" width="100%" src="~/assets/images/banner.png"></Image>
                        <GridLayout columns="auto,*,auto" rows="auto">
                            <Label col="0" row="0" class="font-weight-bold"
                                paddingLeft="10" fontSize="20" color="#000000"
                                text="Đồng hồ G-Shock Nam MRG-G2000R "></Label>
                            <Label col="2" row="0" class="font-weight-bold"
                                marginRight="20" fontSize="14" color="red"
                                text="Xem tất cả sản phẩm"  @tap="toGoPcgaming()"></Label>
                        </GridLayout>
                        <!-- g-shock đắt tiền -->
                        <ScrollView orientation="horizontal" >
                            <StackLayout  orientation="horizontal" @tap="toGoChitiet(item)">
                                <StackLayout margin="10" height="150" width="110"
                                    backgroundColor="#f0f0f5"  v-for="item in pcgamings" :key="item.id">
                                    <Image :src="item.imageUrl"
                                        width="20" height="20"
                                        horizontalAlignment="right"
                                        marginRight="5"></Image>
                                    <StackLayout horizontalAlignment="center"
                                        verticalAlignment="center">
                                        <Image height="50" width="50" :src="item.imageUrl"
                                            ></Image>
                                        <Label fontSize="14" class="font-weight-bold"
                                            color="#000000" :text="item.title"></Label>
                                        <Label fontSize="12" color="#cc0000"
                                            :text="item.price+' VNĐ'"
                                            horizontalAlignment="center"
                                            verticalAlignment="center"></Label>
                                    </StackLayout>
                                    <Button class="btn-rounded-lg"
                                        text="Thông tin" textTransform="none" @tap="toGoChitiet(item)"
                                        marginBottom="5" color="#FFFFFF" backgroundColor="#002e4a"></Button>
                                </StackLayout>
                            </StackLayout >
                        </ScrollView>
                        <!-- Danh sách g-shock special limit -->
                        <GridLayout columns="auto,*,auto" rows="auto">
                            <Label col="0" row="0" class="font-weight-bold"
                                paddingLeft="10" fontSize="20" color="#000000"
                                text="Đồng hồ G-Shock Special Limited " tap="toGoLaptop()"></Label>
                            <Label col="2" row="0" class="font-weight-bold"
                                marginRight="20" fontSize="14" color="red"
                                text="Xem tất cả sản phẩm" @tap="toGoLaptop()"></Label>
                        </GridLayout>
                        <!-- sp Laptop -->
                        <ScrollView orientation="horizontal" >
                            <StackLayout  orientation="horizontal" >
                                <StackLayout margin="10" height="150" width="110"
                                    backgroundColor="#FFFFFF"  v-for="item in laptops" :key="item.id">
                                    <Image :src="item.imageUrl"
                                        width="20" height="20"
                                        horizontalAlignment="right"
                                        marginRight="5"></Image>
                                    <StackLayout horizontalAlignment="center"
                                        verticalAlignment="center">
                                        <Image height="50" width="50" :src="item.imageUrl"
                                            ></Image>
                                        <Label fontSize="14" class="font-weight-bold"
                                            color="#000000" :text="item.title"></Label>
                                        <Label fontSize="12" color="#cc0000"
                                            :text="item.price+' VNĐ'"
                                            horizontalAlignment="center"
                                            verticalAlignment="center"></Label>
                                    </StackLayout>
                                    <Button class="btn-rounded-lg"
                                        text="Thông tin" textTransform="none" @tap="toGoChitiet(item)"
                                        marginBottom="5" color="#FFFFFF" backgroundColor="#002e4a"></Button>
                                </StackLayout>
                            </StackLayout >
                        </ScrollView>
                        <!-- danh sách Phone -->
                        <GridLayout columns="auto,*,auto" rows="auto">
                            <Label col="0" row="0" class="font-weight-bold"
                                paddingLeft="10" fontSize="20" color="#000000"
                                text="Đồng hồ G-Shock Nam giá rẻ"></Label>
                            <Label col="2" row="0" class="font-weight-bold"
                                marginRight="20" fontSize="14" color="red"
                                text="Xem tất cả sản phẩm" @tap="toGoPhone()"></Label>
                        </GridLayout>
                        <!-- sp g-shock gia re -->
                        <ScrollView orientation="horizontal" >
                            <StackLayout  orientation="horizontal" >
                                <StackLayout margin="10" height="150" width="110"
                                    backgroundColor="#FFFFFF"  v-for="item in phones" :key="item.id">
                                    <Image :src="item.imageUrl"
                                        width="20" height="20"
                                        horizontalAlignment="right"
                                        marginRight="5"></Image>
                                    <StackLayout horizontalAlignment="center"
                                        verticalAlignment="center">
                                        <Image height="50" width="50" :src="item.imageUrl"
                                            ></Image>
                                        <Label fontSize="14" class="font-weight-bold"
                                            color="#000000" :text="item.title"></Label>
                                        <Label fontSize="12" color="#cc0000"
                                            :text="item.price+' VNĐ'"
                                            horizontalAlignment="center"
                                            verticalAlignment="center"></Label>
                                    </StackLayout>
                                    <Button class="btn-rounded-lg"
                                        text="Thông tin" textTransform="none"
                                        marginBottom="5" color="#FFFFFF" @tap="toGoChitiet(item)"
                                        backgroundColor="#002e4a"></Button>
                                </StackLayout>
                            </StackLayout >
                        </ScrollView>
                        <GridLayout row="*,*" />
                        <!-- giới thiệu -->
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
        </GridLayout>
    </Page>
</template>
<script >
    import Pcgaming from "./Pcgaming";
    import Laptop from "./Laptop";
    import Phone from "./Phone";
    import Cart from "./Cart";
    import Chitiet from "./Chitiet";
    import Login from "./Login";
    export default {
            computed: {},
            mounted() {},
            data() {
                return {
                    itemSelected: 0,
                    carts: [],
                    pcgamings: [
                    {
                            id: 1,
                            title: "Casio G-Shock Nam MRG-G2000BL-9A",
                            description: "Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/gaming1.png"  ,
                            price: 281990000,
                            amount: 0,
                            info:"\nVật liệu vỏ / vành bezel: Titan.\nDây đeo làm bằng cao su flo mềm, bền chắc\nChốt gập 3 chỉ với một lần bấm\nChống va đập\nMặt kính saphia với lớp phủ không phản quang\nNeobrite\nChống từ\nNúm vặn khóa bằng vít\nTăng bền sâu cho các lớp + Phủ DLC\nChống nước ở độ sâu 200 mét\nTough Solar (Chạy bằng năng lượng mặt trời)\nĐèn LED (Chiếu sáng cực mạnh)\nPhát sáng sau\nNhận tín hiệu GPS: Tự động nhận (thông tin thời gian, một lần/ngày);\nNhận thủ công (thông tin vị trí, thông tin thời gian)",
                            imginfo:"~/assets/images/gaming1-6.png",
                            
                    },
                    {
                            id: 2,
                            title: "Casio G-Shock Nam MRG-G2000R-1A",
                            description: "Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/gaming2.png"  ,
                            price: 172288000,
                            amount: 0
                    },
                    {
                            id: 3,
                            title: "Casio G-Shock Nam MRG-G1000B-1A",
                            description: "Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/gaming3.png"  ,
                            price: 85509900,
                            amount: 0
                    },
                    {
                            id: 4,
                            title: "Casio G-Shock Nam MRG-G1000D-1A",
                            description: "Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/gaming4.png"  ,
                            price: 65631200,
                            amount: 0
                    },
                    {
                            id: 5,
                            title: "Casio G-Shock Nam MRG-B2000R-1A ",
                            description: "Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/gaming5.png"  ,
                            price: 76774500,
                            amount: 0
                    },
                    ],
                    laptops: [
                    {       
                            id: 6,
                            title:"Casio G-Shock GM-6900CX-4DR",
                            description:"Giới thiệu các thiết kế dòng G-SHOCK GM-5600 và GM-6900 phủ kim loại màu đỏ và vàng để kỷ niệm Tết năm 2021.",
                            imageUrl: "~/assets/images/lap1.jpg",
                            price: 7339500,
                            amount: 0,
                    },
                    {       
                            id: 7,
                            title:"Casio G-Shock Nam GA-110JOP-1A4",
                            description:"GA-110JOP-1A4 nổi bật với tông màu đỏ, trắng, đen với họa tiết mô phỏng sức mạnh của Monkey D. Luffy. Kim đo tốc độ (subdial góc 9h) của đồng hồ được thiết kế với hình ảnh chiếc mũ rơm đặc trưng của Luffy và dòng chữ ‘Wanted” được giập chìm ở góc 3 giờ.",
                            imageUrl: "~/assets/images/lap2.jpg",
                            price: 12990000,
                            amount: 0
                    },
                    {       
                            id: 8,
                            title:"Casio G-Shock Nam GA-110JDB-1A4",
                            description:"GA-110JDB-1A4 nổi bật với tông màu cam và vàng đậm với hình ảnh về sức mạnh và các cấp độ tiến hóa Super Saiyan của nhân vật chính Son Goku. Kim đo tốc độ (subdial góc 9h) của đồng hồ được thiết kế với hình viên ngọc 4 sao, một trong 7 viên ngọc rồng cùng với biểu tượng “Z” được giập chìm ở góc 3 giờ.",
                            imageUrl: "~/assets/images/lap3.jpg",
                            price: 7339500,
                            amount: 0,
                    },
                    {       
                            id: 9,
                            title:"Casio G-Shock GM-6900CX-4DR",
                            description:"Nếu bạn thích một chiếc đồng hồ, bạn sẽ mua nó. Vì vậy, tôi muốn nhắc bạn về sự tồn tại của dòng GA-700 , nhưng chỉ trong một phiên bản giới hạn của Godzilla được gọi là GA-700-4APRG và G-Shock GA-700-1BPRG",
                            imageUrl: "~/assets/images/lap4.jpg",
                            price: 7339500,
                            amount: 0,
                    },
                    {       
                            id: 10,
                            title:"Casio G-Shock Nam GA-100JK-4A",
                            description:"Mẫu mới này là kết quả của sự hợp tác giữa công nghệ tuyệt vời của G-Shock và Marcelo Burlon. Burlon’s COUNTY OF MILAN là một hãng thời trang hàng đầu thế giới từng được sự ủng hộ của những người nổi tiếng và các nghệ sỹ trên toàn thế giới.",
                            imageUrl: "~/assets/images/lap5.jpg",
                            price: 17339500,
                            amount: 0,
                    },                    
                    ],
                    phones: [
                    {
                            id: 11,
                            title:"Casio G-Shock Nam GA-700-1B",
                            description:"Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/phone1.jpg",
                            price: 2685000,
                            amount: 0,
                    },
                    {
                            id: 12,
                            title:"Casio G-Shock Nam GMA-S2100-1A",
                            description:"Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/phone2.png",
                            price: 2791800,
                            amount: 0,
                    },
                    {
                           id: 13,
                            title:"Casio G-Shock Nam GA-700BMC-1A",
                            description:"Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/phone3.jpg",
                            price: 2876400,
                            amount: 0,
                    },
                    {
                           id: 14,
                           title:"Casio G-Shock Nam GA-100B-4A",
                            description:"Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/phone4.jpeg",
                            price: 2547200,
                            amount: 0,
                    },
                    {
                           id: 15,
                            title:"Casio G-Shock Nam GA-110HC-1A",
                            description:"Là 1 sản phẩm Đồng hồ G-Shock Nhật Bản chuyên chống va đập, chống nước tối thiểu 200m, wr20bar. Đặc biệt BẢO HÀNH 5 NĂM TOÀN QUỐC! Bello là đối tác chính thức của Casio G-Shock tại Việt Nam từ 2009. Mua G-Shock đến Bello!",
                            imageUrl: "~/assets/images/phone5.jpg",
                            price: 3553600,
                            amount: 0,  
                    },                 
                    ],
                }
            },
            
            methods: {
                onButtonTap() {},
                
                toGoCart() {
                    this.$navigateTo(Cart, {
                    props: { carts: this.carts },
                    animated: false,
                    transition: {
                    name: "slideLeft",
                    duration: 250,
                    curve: "easeIn",
                        },
                    });
    		    },
                toGoPcgaming() {
                this.$navigateTo(Pcgaming, {
                    props: { pcgamings: this.pcgamings },
                    animated: true,
                    transition: {
                    name: "slideLeft",
                    duration: 250,
                    curve: "easeIn",
                        },
                    });
                },
                toGoLaptop() {
                    this.$navigateTo(Laptop, {
                        props: { laptops: this.laptops },
                        animated: true,
                        transition: {
                        name: "slideLeft",
                        duration: 250,
                        curve: "easeIn",
                            },
                        });
                },
                toGoPhone() {
                this.$navigateTo(Phone, {
                    props: { phones: this.phones },
                    animated: true,
                    transition: {
                    name: "slideLeft",
                    duration: 250,
                    curve: "easeIn",
                        },
                    });
                },
                toGoChitiet(item){
                    this.$navigateTo(Chitiet, {
                        props: {
                            item: item,
                        },
                        animated: true,
                        transition: {
                        name: "slideLeft",
                        duration: 250,
                        curve: "easeIn",
                        },
                    })
                },
                toGoLogin(item){
                    this.$navigateTo(Login, {
                        props: {
                            item: item,
                        },
                        animated: true,
                        transition: {
                        name: "slideLeft",
                        duration: 250,
                        curve: "easeIn",
                        },
                    })
                },
                
            },
            watch: {
                
                laptops: {
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
                pcgamings: {
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
                phones: {
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
    background-color: black;
    color: white;
    }
    .title{
      text-align: center;
    }
</style>