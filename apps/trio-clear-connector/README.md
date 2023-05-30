# Trio-clear connector
 
## Summary

이 App은 Trio-clear service에 주문을 생성하는 기능을 위한 App입니다.

이 앱을 사용하기 위해서는 아래의 조건에 부합되어야 합니다.

* Trio-clear로부터 사용가능한 API server를 전달 받야야합니다.
* 사용자는 Trio-clear 서비스에 이미 가입된 상태여야 합니다.

## Features

### Authentication

End-user는 자신의 Trio-clear account를 가지고 로그인을 시도합니다.

정상적으로 로그인된 경우, Access-Token을 받게됩니다.

***관련 API**

* [Sign-in Trio-clear](./trio-clear-login.md)
* [Sign-out Trio-clear](./trio-clear-logout.md)

**Access-token**

아래의 특징을 갖습니다.

* 이 토큰은 만료시각을 가지고 있지 않습니다.
* 이 토큰을 사용하는 Application에서 Token을 더이상 사용하지 않게되는 시점(일반적으로 로그아웃 등)에 Token 을 삭제하여야 합니다.

### Create an order

주문을 생성하기 위한 API를 호출합니다.

Trio-clear에 주문을 생성하기 위한 기본 정보들을 필요하다면 변환하여 정보/파일을 전달해야합니다.

이 API를 사용하려면 [Sign-in Trio-clear](./trio-clear-login.md)을 통해서 ```api_token``` 정보를 획득해야합니다.

* [Create an Order Trio-clear](./trio-clear-create-order.md)

## Worflows

아래의 기본 흐름을 따릅니다.

1. Trio-clear에 사용자 인증 및 인증정보 보관
2. 주문을 생성하려는 시점에 Trio-clear에서 제공하는 상품을 택1 해야합니다.(이 과정은 아래의 과정과 같이 진행해도 무방합니다.)
3. 주문 생성 요청 시점에 Trio-clear에 전달할 Format으로 Data Convert
4. 주문을 위한 API에 Request(POST)
