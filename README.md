# Study Room Booking

Ứng dụng mobile giúp sinh viên tìm kiếm và đặt phòng học, phòng lab trong khuôn viên trường.

Ứng dụng được xây dựng bằng React Native và Expo, với giao diện mobile-first, tìm kiếm phòng, bộ lọc, điều hướng bằng tabs/stack và chọn time slot không bị trùng lịch.

## Tính năng

- Browse Rooms: xem danh sách phòng học và phòng lab.
- Tìm kiếm theo tên phòng hoặc tòa nhà.
- Bộ lọc theo trạng thái, không gian yên tĩnh và sức chứa lớn.
- Hiển thị thông tin phòng: hình minh họa, tòa nhà, số chỗ và trạng thái.
- Chọn time slot còn trống.
- Khóa các time slot đã được đặt để tránh xung đột.
- My Bookings: xem lịch đặt phòng sắp tới.
- Profile: xem thông tin tài khoản và cài đặt cơ bản.

## Công nghệ

- Expo SDK 57
- React Native 0.86
- TypeScript strict mode
- React Navigation 7
  - Native Stack Navigator
  - Bottom Tab Navigator
- Zustand: quản lý trạng thái booking phía client
- TanStack Query: nền tảng cho server state và đồng bộ dữ liệu API
- FlatList: hiển thị danh sách phòng hiệu quả trên mobile

## Yêu cầu môi trường

Cài đặt các công cụ sau trước khi chạy project:

- Node.js LTS
- npm
- Expo Go trên điện thoại Android hoặc iOS
- Git

Kiểm tra phiên bản:

```bash
node --version
npm --version
```

## Cài đặt

Clone repository và truy cập vào thư mục project:

```bash
git clone <repository-url>
cd StudyRoomBooking
```

Cài đặt dependencies:

```bash
npm install
```

## Chạy ứng dụng

Khởi động Expo development server:

```bash
npx expo start
```

Sau khi server khởi động:

1. Mở ứng dụng Expo Go trên điện thoại.
2. Đảm bảo điện thoại và máy tính dùng cùng một mạng Wi-Fi.
3. Quét QR code hiển thị trong terminal hoặc trên trang Expo Dev Tools.

Có thể sử dụng các lệnh sau:

```bash
npm start              # Khởi động Expo
npm run android        # Mở trên Android emulator hoặc thiết bị Android
npm run ios            # Mở trên iOS simulator, yêu cầu macOS
npm run web            # Chạy bản web
```

Nếu không kết nối được qua Wi-Fi, thử tunnel mode:

```bash
npx expo start --tunnel
```

## Kiểm tra code

Chạy TypeScript compiler:

```bash
npx tsc --noEmit
```

Chạy ESLint:

```bash
npm run lint
```

## Cấu trúc chính

```text
StudyRoomBooking/
├── App.tsx          # Navigation, màn hình và logic booking hiện tại
├── assets/           # Icon và asset của Expo
├── app.json          # Cấu hình Expo
├── index.ts          # Entry point
├── package.json      # Dependencies và scripts
├── tsconfig.json     # Cấu hình TypeScript strict
└── eslint.config.js  # Cấu hình ESLint
```

## Ghi chú dữ liệu

Phiên bản hiện tại sử dụng dữ liệu phòng mẫu được khai báo local để phục vụ demo. Zustand lưu booking trong bộ nhớ của ứng dụng, vì vậy dữ liệu booking sẽ mất khi reload app.

TanStack Query đã được cấu hình trong root app để sẵn sàng kết nối API backend ở các phiên bản tiếp theo. Khi dữ liệu được lấy từ server, nên đưa việc fetching và cache vào TanStack Query; chỉ dùng Zustand cho trạng thái UI hoặc trạng thái client-local.

## Troubleshooting

### Expo Go không quét được QR code

- Kiểm tra điện thoại và máy tính đang cùng mạng Wi-Fi.
- Tắt VPN hoặc firewall đang chặn kết nối local.
- Thử chạy `npx expo start --tunnel`.

### Dependencies không tương thích

Chạy lại lệnh cài đặt theo Expo để kiểm tra và sửa package version:

```bash
npx expo install --fix
npm install
```

### Cache Expo gây lỗi

Xóa cache Metro rồi khởi động lại:

```bash
npx expo start -c
```

## License

Project phục vụ mục đích học tập và demo.
