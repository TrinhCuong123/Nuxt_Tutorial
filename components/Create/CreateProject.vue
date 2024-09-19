<template >
    <div style="padding: 0 10px;">
        <h2 class="font-bold pt-2" style=" color: #015DA8">THÔNG TIN CHUNG</h2>
        <form @submit="onSubmit">
            <div class="flex flex-col pt-2">
                <div class="flex flex-col gap-2">
                    <label  class="font-semibold " for="khu">Khu</label>
                    <div class="flex items-center gap-2">
                        <AutoComplete v-model="khu" dropdown :suggestions="danhSachKhu" @complete="search" class="flex-1" placeholder="Chọn khu"/>
                        <Button icon = "pi pi-plus" style="width: 100px; background-color: #015DA8;" />
                    </div>
                </div>
            </div>
            <div class="flex flex-col pt-3 ">
                <label class="font-semibold " for="tenNha">Tên nhà</label>
                <InputText id="tenNha" v-model="tenNha" aria-describedby="password-help" placeholder="Nhập nhập tên tòa nhà" />
            </div>
            <div class="flex flex-col pt-3">
                <label class="font-semibold " for="diaChi">Địa chỉ</label>
                <Textarea id="diaChi" v-model="diaChi" aria-describedby="password-help" placeholder="Nhập địa chỉ" />
            </div>
            <div class="flex flex-row pt-3 gap-4">
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label class="font-semibold " for="chuDauTu">Chủ đầu tư</label>
                    <AutoComplete v-model="chuDauTu" dropdown :suggestions="dsChuDauTu" @complete="search" class="w-full" placeholder="Chọn chủ đầu tư"/>
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label class="font-semibold " for="donViQuanLy">Đơn vị quản lý</label>
                    <AutoComplete v-model="donViQuanLy" dropdown :suggestions="dsDonViQuanLy" @complete="search" class="w-full" placeholder="Chọn đơn vị quản lý"/>
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label class="font-semibold" for="soTang">Số tầng</label>
                    <InputNumber v-model="soTang" inputId="soTang" fluid />
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label class="font-semibold " for="tongSoCan">Tổng số căn</label>
                    <InputNumber v-model="tongSoCan" inputId="tongSoCan" fluid />
                </div>
            </div>
            <h2  class = "font-bold pt-5"style="color: #015DA8">THÔNG TIN KHÁC</h2>
            <div class="flex flex-row pt-2 gap-4">
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label for="tinhTrangTiepNhan" class="font-semibold">Tình trạng tiếp nhận</label>
                    <AutoComplete v-model="tinhTrangTiepNhan" dropdown :suggestions="dstinhTrangTiepNhan" @complete="search" class="w-full" placeholder="Chọn tình trạng tiếp nhận"/>
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label for="tinhTrangDienTich" class="font-semibold">Tình trạng diện tích sinh hoạt cộng đồng</label>
                    <AutoComplete v-model="tinhTrangDienTich" dropdown :suggestions="dstinhTrangDienTich" @complete="search" class="w-full" placeholder="Chọn tình trạng diện tích sinh hoạt cộng đồng"/>
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label for="ngayKhoiCong" class="font-semibold">Ngày khởi công</label>
                    <DatePicker class="w-full" v-model="ngayKhoiCong" showIcon fluid :showOnFocus="false" date-format="dd/mm/yy" placeholder="Chọn ngày" />
                </div>
                <div class="flex flex-col items-start gap-1 flex-1">
                    <label for="ngayBanGiao" class="font-semibold">Ngày bàn giao sử dụng</label>
                    <DatePicker class="w-full" v-model="ngayBanGiao" showIcon fluid :showOnFocus="false" date-format="dd/mm/yy" placeholder="Chọn ngày" />
                </div>
            </div>
            <div class="flex flex-row pt-2 gap-4">
                <div class="flex flex-col w-1/3  ">
                    <label for="tinhTrangThanhLapBQT" class="font-semibold">Tình trạng thành lập BQT</label>
                    <div class="flex flex-row items-center pt-3 gap-4">
                        <RadioButton v-model="tinhTrangThanhLapBQT" name="tinhTrangThanhLapBQT" value="daThanhLap" style="border-color: #015DA8;"/>
                        <label for="ingredient1" >Đã thành lập</label>
                        <RadioButton v-model="tinhTrangThanhLapBQT" name="tinhTrangThanhLapBQT" value="chuaThanhLap" style="border-color: #015DA8;"/>
                        <label for="ingredient2" >Chưa thành lập</label>
                    </div>
                </div>
                <div class="flex flex-col items-start gap-1 w-1/3  flex-1">
                    <label for="ngayThanhLapBQT" class="font-semibold">Ngày thành lập BQT</label>
                    <DatePicker class="w-full" v-model="ngayThanhLapBQT" showIcon fluid :showOnFocus="false" date-format="dd/mm/yy" placeholder="Chọn ngày" />
                </div>
                <div class="flex flex-col items-start gap-1 w-1/3  flex-1">
                    <label for="ngayBanGiao" class="font-semibold">Diện tích SHCD(m<sup>2</sup>)</label>
                    <InputNumber v-model="soTang" inputId="soTang" fluid disabled/>
                </div>
            </div>
            <div class="flex flex-row pt-2 gap-4">
                <div class="flex flex-col items-start gap-1 w-1/3">
                    <label for="nhomCongTrinh" class="font-semibold">Nhóm công trình</label>
                    <AutoComplete v-model="nhomCongTrinh" dropdown :suggestions="dsnhomCongTrinh" @complete="search" class="w-full" placeholder="Chọn nhóm công trình"/>
                </div>
                <div class="flex flex-col items-start gap-1 w-1/3">
                    <label for="duAn" class="font-semibold">Dự án</label>
                    <AutoComplete v-model="duAn" dropdown :suggestions="dsduAn" @complete="search" class="w-full" placeholder="Chọn dự án"/>
                </div>
                <div class="flex flex-col items-start gap-1 w-1/3">
                    <label for="congTrinhCha" class="font-semibold">Công trình cha</label>
                    <AutoComplete v-model="congTrinhCha" dropdown :suggestions="dscongTrinhCha" @complete="search" class="w-full" placeholder="Chọn công trình cha"/>
                </div>
            </div>
            <h2  class = "font-bold pt-5"style="color: #015DA8">Vị trí</h2>
            <div class="flex flex-row pt-2 gap-4">
                <div class="flex flex-col items-start gap-1 w-1/2">
                    <label for="quanHuyen" class="font-semibold">Quận, huyện</label>
                    <AutoComplete v-model="quanHuyen" dropdown :suggestions="dsquanHuyen" @complete="search" class="w-full" placeholder="Chọn quận, huyện"/>
                </div>
                <div class="flex flex-col items-start gap-1 w-1/2">
                    <label for="xaPhuong" class="font-semibold">Xã, phường</label>
                    <AutoComplete v-model="xaPhuong" dropdown :suggestions="dsxaPhuong" @complete="search" class="w-full" placeholder="Chọn xã, phường"/>
                </div>
            </div>
            <div class="flex flex-row pt-2 gap-4">
                <div class="flex flex-row w-1/2">
                    <div class="flex flex-col items-start gap-2 w-1/2">
                        <label for="kinhDo" class="font-semibold">Kinh độ</label>
                        <InputText v-model="kinhDo" class="w-full" placeholder="Chọn kinh độ"/>
                    </div>
                    <div class="flex flex-col items-start pl-2 gap-2 w-1/2">
                        <label for="viDo" class="font-semibold">Vĩ độ</label>
                        <InputText v-model="kinhDo" class="w-full" placeholder="Chọn vĩ độ"/>
                    </div>
                </div>
                <div class="flex flex-col  gap-2  w-1/2">
                    <Button icon = "pi pi-send" style=" background-color: #015DA8;" class="w-full" label="Chọn ví trí trên bản đồ"/>
                </div>
            </div>
        </form>
    </div>
</template>
  
<script setup>
    import { ref } from 'vue';
    import 'primeicons/primeicons.css'

    const khu=ref('')
    const tenNha = ref('');
    const diaChi = ref('');
    const danhSachKhu = ref([]);
    const chuDauTu = ref('');
    const dsChuDauTu = ref([]);
    const donViQuanLy = ref([]);
    const dsDonViQuanLy = ref([]);
    const soTang = ref(0);
    const tongSoCan = ref(0);
    const tinhTrangTiepNhan = ref('');
    const dstinhTrangTiepNhan = ref([]);
    const tinhTrangDienTich = ref('');
    const dstinhTrangDienTich = ref([]);
    const ngayKhoiCong = ref(new Date());
    const ngayBanGiao = ref(new Date());
    const tinhTrangThanhLapBQT = ref('');
    const ngayThanhLapBQT = ref(new Date());

    const search = (event) => {
        let _items = [...Array(3).keys()];
        danhSachKhu.value = event.query ? [...Array(10).keys()].map((item) => event.query + '-' + item) : _items;   
    }
    const onSubmit = () => {
    alert(`Tên: ${khu.value}\nEmail: ${tenNha.value}\nMật khẩu: ${diaChi.value}`);
    // Thực hiện hành động đăng ký như gọi API
    };
</script>
    
<style scoped>
     
</style>
  