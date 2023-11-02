# react-native-final-tree-view

A React Native Tree View component!

## Installation

`yarn add react-native-final-tree-view`

## Usage

Firstly, you have to define your data. Example:

```js
const family = [
  {
    id: 'Grandparent',
    name: 'Grandpa',
    age: 78,
    children: [
      {
        id: 'Me',
        name: 'Me',
        age: 30,
        children: [
          {
            id: 'Erick',
            name: 'Erick',
            age: 10,
          },
          {
            id: 'Rose',
            name: 'Rose',
            age: 12,
          },
        ],
      },
    ],
  },
]
```

It is required that each node on the tree have its own `id` key. Obviously, it should be **unique**.
The tree nodes are defined in the `children` key.
They are an array of objects, following the same structure as the parent.

After defining your data, mount the component. Example:

```js
import React from 'react'
import { Text, View } from 'react-native'

import TreeView from 'react-native-final-tree-view'

function getIndicator(isExpanded, hasChildrenNodes) {
  if (!hasChildrenNodes) {
    return '-'
  } else if (isExpanded) {
    return '\\/'
  } else {
    return '>'
  }
}

function App() {
  return (
    <TreeView
      data={family} // defined above
      renderNode={({ node, level, isExpanded, hasChildrenNodes }) => {
        return (
          <View>
            <Text
              style={{
                marginLeft: 25 * level,
              }}
            >
              {getIndicator(isExpanded, hasChildrenNodes)} {node.name}
            </Text>
          </View>
        )
      }}
    />
  )
}

export default App
```

This should display:

![First render](https://i.imgur.com/LWDr9Ba.png)

And, after a few touches:

![All expanded](https://i.imgur.com/lEWGnIW.png)

## Props

### `data`

**Required**. The tree data to render. It's an array of objects.
Each object should have, at least, the `id` of the node and the `children` of it.
This structure can be changed via the props `idKey` and `childrenKey`, respectively.

### `renderNode`

**Required**. A function that must return the JSX to render the item. Signature:

```js
renderNode({ node, level, isExpanded, hasChildrenNodes })
```

Example:

```js
function getIndicator(isExpanded, hasChildrenNodes) {
  if (!hasChildrenNodes) {
    return '-'
  } else if (isExpanded) {
    return '\\/'
  } else {
    return '>'
  }
}

renderNode={({ node, level, isExpanded, hasChildrenNodes }) => (
  <View>
    <Text
      style={{
        marginLeft: 25 * level,
      }}
    >
      {getIndicator(isExpanded, hasChildrenNodes)} {node.name}
    </Text>
  </View>
)}
```

### `onNodePress`

Optional. A callback fired when a node is pressed. Signature:

```js
onNodePress({ node, level })
```

It accepts a promise if you want. If you **DON'T** want the specific node to expand or collapse, return `false` at the end of this event!!!

### `onNodeLongPress`

Optional. A callback fired when a node is long pressed. Signature:

```js
onNodeLongPress({ node, level })
```

### `isNodeExpanded`

Optional. Used for custom handling of expanded nodes. Signature:

```js
isNodeExpanded(id)
```

### `idKey`

Optional. The `id` key to refer to. Defaults to `id`

### `childrenKey`

Optional. The `children` key to look for. Defaults to `children`

### `activeOpacityNode`

Optional. The opacity of the wrapped node. Defaults `0.2`

### `initialExpanded`

If nodes should start expanded. Defaults to `false`

## FAQ

### If I modify the `data` prop does it reflect the changes without collapsing the nodes?

No. Once you modify the data, the whole tree goes back to `initialExpanded`

### Are PRs open?

Yes! Feel free to contribute!

## License

MIT



# HUE_SMARTKIOSK_2023_RnD

Xây dựng và phát triển Kiosk cho các địa phương 


## TECH STACK

**Client:** HTML5, CSS3, jQuery, Websocket

**Server:** ASP.NET MVC 5, ASP.NET MVC Core 7.0, ASP.NET SOAP 

**Database:** SQL Server 2016 


## IDE

Để chạy được project cần cài đặt các ứng dụng sau:

**IIS:** https://phatthanhdat.com/quan-tri-mang/cach-cai-dat-va-su-dung-iis-tren-windows-server-2019-73.html
![IIS SETUP](https://lh3.googleusercontent.com/pw/ADCreHfJ-4_TBsvUlbanmmAv5hUXBEv7wbis4aOwGEmWcUkdESZLDLm9Sa0s_LnFvlZhBEOrspQfq4l4cQR_RwiQitUKDOpRfUmRUDyzV_7D6bAmz57NGPb_-yWHw6LPyHx8Q9DRrkB7lZElvqaX2z_Znmamz0fL2MmlAwEFQ2AX3Ijp0JndqNgkmMW3edalBo68_u9NHsqfP3wCRiJKb9SwjnhsDyoUeQ8w2gmixkgn6UnLzvNvshDGVye558zC2YxbRfxUXa88onpAumvNZErK4SCu4eeC6hdreQ8ue8S0eKl8g4WV_UnaP1k1zIuvErQmWAi0atyd-Y_E_tV2SxRN1xEU_OM4CJ6jJ2brc74O2u8N-ba0uW1BnPexDKN3fOIEgoRbGyuZ9jKfn-nh3KANRhb-HnFXoButo3ceJQc-2kcrAmwW9QTYF737O7lVt1oRRI--xAfDiU9TqxS_yIuCEehBCKlM9XmiGcYuIL71wBROqFoPleViwKSM7fjeEVgQ8-aoXx8L9iunscnSBnZCQRfv5YR6E0KCpCzwJtju1Av4y7ns_-riVYK3tNeFtbNK6_DyjL4bUnxIBmgziqLNtXuYnglEP91nnzvt4Ho3mKljhfUS5pj4crWHV-JCxCnyZPr7EwIaKrj8j42S0k2aXo-aOJvb-WUs4XBDo5UN4tgSDkLEdlUuB348raeD06F7GsiTu9rnnEC4us74YcfBgXxo3NmRYO46wzDWWbw0ooTxTVR0E47PZvf6NqN-nCd4oa-6Zj0p_MSyiisyrMl8pGaxlDgr6LYPUY6bihznoBtTQI9SdzSXY0ZBDfudJkG4ma9hX7QxLDPYpL9NKxNB8QFF4t9DEuApbr827bGTtsaet47WLVeQxJHpE5yKdivvbhv6E8MaykjvOC7C47VbC2s=w562-h205-s-no-gm?authuser=0)
![IIS SETUP](https://lh3.googleusercontent.com/pw/ADCreHdCX1o83wUI_tLeuokmE7hdBl_3gGGj_MDPp6-6ta7pCGo0TLm3DD1dZUtFAcyOG9V5F4OmIXSmLWjdiuhQo5H6imQb69mjLpEfBzudGh_t-whQ-qWT2ucvJ9fmWDanv7_TjESdLNkjWtKf8CZrqa0fSA=w435-h886-s-no-gm?authuser=0)

**.NET Core SDK:** https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.403-windows-x64-installer

**ASP.NET Core Runtime:** https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-aspnetcore-7.0.13-windows-x64-installer

**.NET Core Runtime:** https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-7.0.13-windows-x64-installer

**.NET Standard SDK 4.8:** https://support.microsoft.com/en-us/topic/microsoft-net-framework-4-8-offline-installer-for-windows-9d23f658-3b97-68ab-d013-aa3c3e7495e0

**Visual Studio 2022:** https://visualstudio.microsoft.com/downloads

**SQL Server Management Studio (SSMS):** https://aka.ms/ssmsfullsetup

**AnkhSVN for Visual Studio 2022:** https://tortoisesvn.net/downloads.html

**AnkhSVN for Visual Studio 2022:** https://github.com/AmpScm/AnkhSVN/releases/download/v2.9.87/Ankh-VSIX-2022.zip
## 🔗 Repository
[![svn](https://tortoisesvn.net/assets/img/tortoisesvn_logo_hor468x64.5e0587de.svg)](https://svn.hcm.fis.vn/svn/HUE_SMARTKIOSK_2023_RnD/trunk/WIP/Program/SRC)

Sử dụng tài khoản mail FPT *(bỏ đuôi @fpt.com)*.

Báo PM dự án phân quyền vào **Repository** nếu không có **quyền truy cập**
## Checkout and Open Repository

Tạo folder theo Mã dự án theo mã dự án trên Jira (ví dụ: **HUE_SMARTKIOSK_2023_RnD**)

* Folder Dự án
![Folder Dự án](https://lh3.googleusercontent.com/pw/ADCreHfOHsSETE76wI71cYZdjJGmn_SXSXqNIKQD9mko-9BBh-ZL-4w22IITQ3OVf42CTxtb_ikEkJMnqhxg_wjB6KpegFOj89fkQJHkWmeruEcqiV4k6EtBw_hW8JL7yUd-GJDG-wfl8h6gCCura-4Zxe1mvi4ox9xmbHAhhq9C9FU_7X-0PX0QkYFdYvJYcixH1rbsV6pKoMUUU-vDa8zf7P6HFFB4okQ36HiMaXGbTjFZKd9Uk6zV3DnrCH2ZbEoFjzihMdPLdCacVX_QHxnOU6uAJEI27xYLYUXsG6knMGxCgz3YmUl4S2NWUj7RELG9hrBYlu5DbNixxvarh39y98mbz5RtKmSrvtGmnSru8ob2Rw_QQdqrMrNVmXf81fq0XIlkDev4-nrbi6teYKHyV_MMLslR2SLgT13_cADcfvy-AMcDOvQgpt4IufRDsEs8F2-8OODKtC_P67CTeO7WegHEUqhO0l37YChFJRqzG-sZoR0sqICtZfOnhhdR1W7M2Y5aQG9msiMRTf6V6jFiUvRVDG5mqqNS67pgawjBpADOcmnsorI8guMko-CSLQytP82ok__4XqtGlCf-nKFi8TRK41COxtEeUbyh6tycxpokfd7g0_O7RtqR_mUKtd3mBNFhgDLhCu7qr9A7k0QEYpOPKkQrjbnaoZt4iF4kAPF8RwSRDhv68geM-Y8oXRdUdIM253M-A5f_RpYOkQ2HMADtw-fkEL_io2YjZ8uMin6QWd-NNlmbb4dh6BNgWpFz_3thHp4tlI4qkBszQsd99tWhAAC9SIT5Z6paU5o0-3D_19C9MuJQp6UJn23hpk6C-ldeQmNgGK-rQ3Tx1fV-XX8L1SGH_m0CRu8h0e_F4HnUIDWw8oBeJQ-Ly6mtj_PiJ3_xAY0IN77ru6LU_8rzj9U=w569-h39-s-no-gm?authuser=0
)

##
* Checkout SVN
![Checkout SVN](https://lh3.googleusercontent.com/pw/ADCreHfTRrExa_k-ZWwTTMqCTVhEBco5wLWyb5IFPxVTVeaS3sD1sm9O8ClLxtzocP6ppwidIvxl9M64FoxGPamsyBwMyBVwvT1BvYINM4JmJgWZLGes88c2_u-34l5aXIa-QEMrvv_iM2h4CUJJeC_eDlTfK7_W0ScLh74zEGOX3FJ_FG3PVxKqryOGY_yV7auxWJUs6CV0FUv3wZIMI4gQ0ledsJgKS0g6CFHgGJDw_uTwtmehjbLUqGgcRPS3HryizJrTB6u4UJOBfRUgW3wu5uxxQcIM6SO2-iOtwuEDMLA5nJ09F3xsfnsBirgspWRCJDbBJZrTSjQ6bmoA1PvNztDQ9Yu9i70ZBfZE8XV8RZpDy9ZcKmyXtn5tC63uohFy8QYUyU1hYhfhEoeN9nIHDES46yutHQVQNev3bl_6XYqukrQq2XFg-DVqbHvIZj95q2H1xYYK2yq-bpDN55kBuNeKr44JGL07WDjI4-8Pyd23b1VRHbAHHd9KwP9Ap1gl_2EylXUHQFRXlSGuOTsErdVCLTUunZPG6nyek8gkEW-0H3GACgF80mnD0xkjW16MyOrYp-12txwPhIIUuSAyiHkQIGI81L3n6eNzBk9fEtBpjsA7aK9rsH2bdpAhXp4I0iZtHqCKc83NCfufyWWMHmyKAAPPyz6itLWVqbT-vI3pmm7ZKOiwO2T6WsVFve_kVxhNjFGCsZSWlso6MQlXiGHr0LIIamkjm3kNiBqdPl67snL4Xo5V-55ecm8YGTxS6SasCHYq2S4MeT1TfkNuK7OXOkbuud3pHKEL54V2OcHMV6AkfCOBswI_eSItk249Rt5z8DN_DeYuuMrhanwJO6MpHp2rUPAc5OQCC3SW8Fk4d0oceDxbiRaN2yYSYhdzpux41bE4N_mAKEqfFTFloAU=w549-h410-s-no-gm?authuser=0)

##
* Nhập địa chỉ Repository của source code tại trường **URL of repository**
![URL SVN](https://lh3.googleusercontent.com/pw/ADCreHctRlMxJ0fGb0WjXgWsLM6McWoBv1d-Ly1GvjEADEtxPgJyICBoYBWeKq3AsdsIFCaO_dmorRJZpwQqTyEs8TkPJkOFftmcDEvBUeB-AT4i-Fl5BOxkyQ-kO8osPT9VRUPtcOSVkKua7gF5wLi6Z4TY72MGttuJnKZJyjfb-mxbDz24pxtF3zmcTtTbHqqn1cBztrW0qanMDHq2mAmxcgn2mIO8aJ_wPJBXSbF_4C-ORtdW7bytNj_cRcQLHz6hvK138H2mUK747piCBFti_qbm6Xlncz6UxQX5mDFalpGoCkcd70IuFsDtdBO7dV-MmCCusiOU8x9hMiFggjVNu7i4gMLEGTBsvwU_Qz8kmuxtOxNvtQgASA0yoWZWORRqr4HzYlWNdq5BQCjmiFJy6-afnx50FQDD3cP744TydIWtymLlLpElz4Qh2lL6EfjgbfjpNkYJpHfs4yPEExt2oWsSB-nlvFTLCBFnv-KYzzW0GAXKUsQgdlQlZqoKrv9ssshIxsjF46hWSjG5JkPGomqU7lF3k5HkJI2e4r8y2JIIQLvXQi-cmQm9RZ0b2cNVi3v9R3beuugLzoKBKRHaoBUpGfdHNlYVK7id0Lqe0yPemfReG2zr7k4jlpvb_AvavmnxTsY-K74bDW9c-PGCvD1pIhPSZCHw_RgVrIE2oc-YoQVz4YQs7UCZMdsSse-Blae4NMpbjqbJTDGSpxkG8ryR6C0VYt-Oq-VyYwPU6CWR4CzXPEKmjsJS_6nnkrQBf7EWxdIc_EcB_8Hry96hvbuJ7K4tdbRHA0rOkw8V6NKLxB-Doa6IrHi4RYI9CWD8ak4hDXqI2JI9OeVzLaHFgDj5RCHSRk_Xuy26_qW6rGmgfmSgMTNEc34pe8bXonXW2PZVRLh02aP0mqfJKAExIfY=w910-h452-s-no-gm?authuser=0)

##
* Khởi động visual studio dưới quyền **Administrator** và mở solution đã checkout
![Visual Studio](https://lh3.googleusercontent.com/pw/ADCreHcZw9UE9kL0Koql1klaekywEHT8_Y525v5DDJHgSpu6Sz7ckAnxa64WpSoZewAtFJcGTe24kZguUa9jelyM6MdX4JFJXqt7LBoMBOoXqsUBPd2txYlSD7NzDhQgFz8ctssXf9QRSvHac8iuWvTpJVZhFgmfsty0zVyG36hrK6Fdh7SvsOVItksPl4aMZCaippFXNwywkjU3QRlpo4cVE-PVcXowbu9TkJkrEAglZsa57nUe-uXaSNE1DLfWfDspg-ro4jdZDniFmyu33duUzfxFuY3xzW_sQwCT7bTTJcPcsJQSrLnoZb1XjftVVN5v-Z_G17HmR7pw37MdjTmHt-HpvmmSBCZJHGIq1J_OKxpNbc6TsJwkm-aK3q7rbtlPu10XXWCIfayLI--q9Npjy1hBpxGvQZA-a97W9C5Vgp8TbAMaYZmyTovgnQjThRwGz8JnZFXf3xfEEduYBPvSgbfUSfclwfHFmjQgtUb7pCLHqyd5_Ro89SN4D0UGdDfOH5iyKHsnKJM0HZeRvAbLEI2YdO8DZ9YWvmBYJravdBWfv32lyk4Nn6erm5Eg_hGKmbMn5tN74p15bi5ZEjdcxebQ2aqbGXsakafyTN2MssC7fm6k_arQUs8nOG-eAMD6yuTGxFCkisIC18pxvgedhPLI0iDFk_GcevEoShWMeW-9KendAY_YynfhfMjYxRQqo5-wryXuAGgZmpXjC0HixcU1NcwMgwWSary33iOYTTLWn2MLdheZwuieDr7OxkJlvkXsKRT_Nkq21K6x-rmyr3AFVL-sk3PDh3jv3QOYBTXF9Zw63LxaYbng8ZM288uHLdyhTL5UYty0EWK_Puv4Fn76Y-Hxnly2rEponUyAIAIq6gP4cphdMSAjCzhivDQuqMpr7yCx5TlvuCWt2PgYJOY=w349-h628-s-no-gm?authuser=0)

## Run Locally

### Admin

* Source Admin nằm trong thư mục [SVN Path]/Admin
* Mở solution CMS_Solution.sln trên Visual Studio với quyền Administrator
#### Cấu trúc source
![Visual Studio](https://lh3.googleusercontent.com/pw/ADCreHdNEr6H3f27V85XxUwh883LPCrVwT_E2gnS6VDwSz2nVBiBjMgdPaDjIU532gzeQHevbw0T2r-UboVlSC5cx4DuBVvStKvrf8aXE3hY0x6yDb0QyFsb-ioeFKplUIxWCo3pk32WcGWRSJ82XPV976-w8bEJl7Mol1LHTMPbM_r5LuPJ__O99KZXcVikPf3lMdboL5GAA0BhyQkmd2-sspbgY8vTpwsRZ28LXtn_lYlaABZwOAGtMTUfCiUXcEUpS60F-SO1XEijzpT3VFYKRzvt77WO2RxM6a1QfIFd-s20ACLq8u6OpqDv9K0WW3gdTCwY7Dle9E2TrSRL8ruD43GHuvPpUK0D0ms-NWThVVhm4mN7kOj3egKtVIUsaQgywCVtkI3Aof46C1c9FBtlDpsT6XA3o20iD86QhpzhpEHBQQiVTPbmld8cNOp0E3UgZvTSaRo1S6yLRXXxA4XYgOL8SfMdVg_y1rvzTrlZSLkUEiXbGPFCs_qtufukyh8ntcfct-QgJhyQn2-VIfVV7w-9Krt6EKlWsAV0Jr0hBsIY8XgxM2tts5CAv0zlnfBY9qOAx8tzpwu_eR9ukxKrvZ3bEM-I-wTxTOhq9yBo6HRMk6iKGyvH7MXfYd81erPnU1T-SPW_bi2VOHxRZLldSBDN53Mmb05I7FV594iadEicrOwsuTu54ub2BZUyfuyRNwIhYlrEYkgpie3HZ4ejcHe495iqZpwI1LvQkRItiCNjoKjZtqVj1yWDJA7L4A_cPgp1gqZZtbxMMQTe6p6v8YrVCh4px5HBmnZ_VrIr8RHhTlOwb8eSQFIX9Y-9QiVkFb7-m0SxzM-FmjSgwLe6USAURmLH7-WsmdHXFGKQ36P9jPYe0b9S-XRGXqRQ4Lr58Keb_3mpssjPsfHay9Vp4Io=w336-h271-s-no-gm?authuser=0)

* **Project Core.Common**: Cài đặt các hàm hỗ trợ

* **Project Data.Core**: Tương tác với database thông qua thư viện **Restsharp**

* **Project Business.Entities**: Khai báo entity model, định nghĩa model DataAnnotations

* **Project Business.Services**: Lớp trung gian xử lý nghiệp vụ

* **Project Host.WcfService**: API gateway theo chuẩn SOAP RESTFull

* **Project CMS.Admin**: Ứng dụng web MVC tương tác người dùng

#### Cách dựng source

Sau khi check out source tiến hành dựng source lên IIS
* Tạo pool IIS cho quản trị

![Tạo pool IIS cho quản trị](https://lh3.googleusercontent.com/pw/ADCreHfyQeleGaWZtGIsKvtOYN6p1t040LpyaMETt-iWrWwABvt2vkHT_8GdmjrutggRTHqY_gSHWwX3iTNjiCV4GpDx7G9SVy4mBSx5AdEC8yJcYeBdUFfNw7HNBEbfT6h458frrz-T12teiHFUWu1ChAVNNMdLUs6vpvYr5pgJBsartVVMWi7xDoVyfHMAVWGpm5hNC2zEBj2hw2p8hQxFXLS-14IgXBvm1QLRxZKrzbIevFe4QdW0aIk4GYv3BHl3QSn5lGr-LnjaOuml7apylK-HNcJiu9J3MJjh_eK5mXVvwOdOFjNkNpqvJ5GUWYTEmc7Taw5OzycLtwHSQDeniUgctMLzmCSjs8pZvxnFjlfGuS9_aiDLsZqnWDy7ukIHPSmK0UUldlxHh9fmFD7IG3yrzkpo5KqQ70j9GJ36FXFz66Lgemr-zWNsQoBi3zuiHghG-PDYFFtDk4VTTP_2ag-6TZa4pLtzwXPqEGexeShuLVYGvR5RxndHLDc5ZBI4ytsU1GagOaHnSJIo3rHeQCrTyfUmL_-WpXMaph5yJ4vPDHut36-KnwdUCnBfijpS3cj4qKj7cHnNAv5cFggeJm5BI-5dHHkf3XaDtbKpc5epPAYKtCsk3-NwsrvKljq7OmtEI9UxKYedBdn3inRDSv9_LZaxa2Qd08wm9IWxrEpn-3PIZkSBvykgSoO7JXmrgnv8_EpRuB-JUQ7NggadSiUBLRNqCr9djRiC6xmUuaFOF9juaOvGyD0P4NwYL3EcsWgmqwrOFuc5GrKOOLnigv5rXZC2VHqgxGEQDw6uatyiTLgVcdP26JgFxC7_dbW9ior-lwzVpyBZH5RMPDaS3MMNQaQg415ZBtvd83ZaKtryKYm_ygK4QF6jrh-h_TDheM0b_bnPEbQvjlUgJfMwzUQ=w395-h123-s-no-gm?authuser=0)

![Tạo pool IIS cho quản trị](https://lh3.googleusercontent.com/pw/ADCreHetPUZz3zAP7tDFXfqGzvw5dC2eN6UINfFw4TKPVC-tnT1fYjivMGC-3WOjEBLNv8jyKS-8TcBuGXXzCFqL8OQDjv2k3QAKI2V_E7bHbyW6AeldnZFMxhmY1c4f3_LU8U2bfbcdSMtBQYd0S_enYRq91rhv9ysUjhnkmwsL5joNCzPLjuekj7tjfniaC-susu5Ql3GihNxC_TZVr-QR5vznbagg53LKHij0DQBEIWixulVItGvYPS8VHHuEmTTgAUwTMQTNaaC1ZZ6l8aYkgqKv_7EDSttla5zsVLTx3dFi4xJUnBUDAnfDQgXVyDpMJUebPaKJniWTbq5qZfFemSFJtqOU-V9I1mq_fQgSwPNULM34WHq3-x1VTNld-ze79SNez6hOQ67A8WWE42s6zjiiPT1bli_MSW50P9Q8OUdfefJDqyLJ5NdOfrqDywCS_hGmRvJKc7-PGIIu45pDrbJNZ1aOi-nRCyH5UughkIcuJWNk28x0dOxmax935yW6I4Cn2Wkc1sB2oDOHBm6AGCrzwjW-KIGf74G1lj1rQPOAFjeyyIPY96CfMDGfrKdO-Qr-gUaLzikYs1HsZXzA9j4O8PSB9JoCEqEFn9bDg0fejA_rSrdVy0t8xEdMqXWdB1Bw_0RdR5-k4qcDAWoWCU6MkHcuYXA6d-4R3oucFQ6FQpI6Ijxb0jvgO7s86zLoUdscLHllvOmHwn0m8PydpV-LFl2uhZd_28diIOcDo1j1lwd0Cbj5gBC6HCQVLszLMzaDwUjxglOKuThnNRO8vFd334jKqeqjIVhqpTityQnQ5VQPg1m_T9yhth9XaNJ29PCHB12_EsCZNx0pMSvpgZLNapnH9PIHYM9XlOSdLiOY4Q6_laxWhW4Pz2wuNz7BYetf2sHO3LMmyUFkKrZRedE=w325-h334-s-no-gm?authuser=0)

* Dựng services: 
![Dựng services](https://lh3.googleusercontent.com/pw/ADCreHe3qRE5yIGgk3YWeFgP5b80dB7fxXHmWRn7k6mv92fVaj99wNkYYCy8e0pUsSw0LsiiQ3FiB-fkbWF4DFYyjwgOMqGJY48sRBlnuYZzYsCE_k1bIfF2OuueYvlsw1ZlhjEJaQnVbSUA_ZZzYQpijwVB2CFwYl5f5x98SZE_Avw3i8SVjjuCpM9EoDu9nVY7Z3PS6hmzw8f-APnfys0Vdyvyr9gQcO_BkvxZJsdOc-7ln2NvPGgU83HLgY52p-lgVrzbz7i6RbGMDKAS01Z72ziM1wF5ivK6X0XqecTweFg33ikVtW0mZQG1Ad65yn8r62-zl72nwDk96i7X2-tkepfzVgQdBUHX2UF8PKdTlTogzXRlIpHP7JWvGEYxIeypkluhSgC2ggEqbfwq6yYzAwh7Vn_cc1TXn7KGC2wwAUg_PCttsPDDu61AE2C59VAPbZZ3isGsFfjzEygroJXcAnUTgie6-vKpMW0B7TPuVk91E9JLOa0VM_YE-gr4dzuc8aL71HBctm0KrJeUunL4jvKXddHUHTZZ2OyCO4B-1fjsdEdRP5-AAtpiLu3ZTXufpsb1wSYo3NoXs9Tq8oAbbuKakLYCgd45gC5uvSMWxgeBv-u6jTR2viCRz95fkUpBz2fib3vPOrX7e2P1HqmNFBmpiYQtYbTp-bTeyVQPOU9sibPX1FcMU9hfUk74279pgPWymLJOi86778ML4PhlQDOlvDvbJY2jg3vzBsWHv7OUyr7BSVrP9k6WyRneOUd3T92kUxuvfY7dLbrBbLd8sLXI-EN4LYO6zOXEBCnoN7MMDWm09eHGkl2P812YFGTSgMqBTWxsyccFcG5MorJ5o4Bu_0qN5l_LvxlQCMHvoEdtBDk99iebli7kIqddii9ZH0pzWBhSTFQjyuw4XUZb338=w311-h432-s-no-gm?authuser=0)

![Dựng services](https://lh3.googleusercontent.com/pw/ADCreHeeQpAwZlJA09yuTdSjdHwM7CK7Unp7obLFezOz2h2U_vyBB9xQsQDCqBHAMqAO8t3LIFS0bn_RKbzE37OhKS-J7UTw_TGGX3VKLjpCOFXrr-8kjO4wHGuZgxZJ2mSGmFfZyZXBtJUiRQitOhIt8VacZz8EeNkBeja6OsqmAZZnUOPwmN7yOBlQFIYNKttRhvxlKoC0dXHqIZBn29P7G_2y0zgqRbZA4JP2LrSVVEHtbvQsNvh0_xVCawqxOlKdoz9gP41FFxfrLxDIKqTm-s72OTqXt7S_pJLW6UTGvhsDtWgwoCTB2k970y6hwTpKZgk3tRCQDWr4hN_4ggsx0t6ItcFr3ukfuVPcZgS8vqQgXTzHkd2xWlGHKkKxFytA60PvhpjF9Ik_0Ju5BGUhr4FdReoZpqGuoeSrmTwKU6zwfzN46RXkbVj_6WqZx-VDEQgJE7Az2m1v8y3UtOJTTkVuqudd6RB4U807E08SkhECRDgNCXmYaTjf1rDobigHLdDcTObtoEWxUVwXFsMPPjDfypjcio7PXhoUc2V2HKVdg7Kw56_qCWG2lp84tNqmnRAPHuj8IHPOfUoPE1e5DZ3gNqU4mxiiTxSqGmHYfurmWnHLukWv4Tc5LWAMELubrSwVDk8E-WmCD9cOY1hfy5gdqet4_kycBOGdgQ89447l0mgQzcVqNZpNazT02iDng3N03UJRfMR5aqGChsknJ1Tl3aaFZuO-kwl4Fzk4yMhO07khCoVMg4ebaLKlo3dRhzxAKv9An2p8jHzWWeXg9lVY2_bPt62MDf4CJJCDtWlxk0SaKH46NPrU8y30_4m9135xgEnJi6OUR6asIKpMwWvLMsf6FI9lqG6aHDJx_nY8hmqS9vBq5aJBDERbwtWJZJUYv26bkottuiNH1W1wv4M=w585-h682-s-no-gm?authuser=0)

***Site name:*** Tùy chỉnh

***Physical Path:*** [SVN Path]\Admin\BACKEND\Host\Host.WcfService

***Port:*** Tùy chỉnh

***Application pool:*** pool đã tạo ở trên

* Dựng Website quản trị: 

![Dựng Website quản trị](https://lh3.googleusercontent.com/pw/ADCreHe3qRE5yIGgk3YWeFgP5b80dB7fxXHmWRn7k6mv92fVaj99wNkYYCy8e0pUsSw0LsiiQ3FiB-fkbWF4DFYyjwgOMqGJY48sRBlnuYZzYsCE_k1bIfF2OuueYvlsw1ZlhjEJaQnVbSUA_ZZzYQpijwVB2CFwYl5f5x98SZE_Avw3i8SVjjuCpM9EoDu9nVY7Z3PS6hmzw8f-APnfys0Vdyvyr9gQcO_BkvxZJsdOc-7ln2NvPGgU83HLgY52p-lgVrzbz7i6RbGMDKAS01Z72ziM1wF5ivK6X0XqecTweFg33ikVtW0mZQG1Ad65yn8r62-zl72nwDk96i7X2-tkepfzVgQdBUHX2UF8PKdTlTogzXRlIpHP7JWvGEYxIeypkluhSgC2ggEqbfwq6yYzAwh7Vn_cc1TXn7KGC2wwAUg_PCttsPDDu61AE2C59VAPbZZ3isGsFfjzEygroJXcAnUTgie6-vKpMW0B7TPuVk91E9JLOa0VM_YE-gr4dzuc8aL71HBctm0KrJeUunL4jvKXddHUHTZZ2OyCO4B-1fjsdEdRP5-AAtpiLu3ZTXufpsb1wSYo3NoXs9Tq8oAbbuKakLYCgd45gC5uvSMWxgeBv-u6jTR2viCRz95fkUpBz2fib3vPOrX7e2P1HqmNFBmpiYQtYbTp-bTeyVQPOU9sibPX1FcMU9hfUk74279pgPWymLJOi86778ML4PhlQDOlvDvbJY2jg3vzBsWHv7OUyr7BSVrP9k6WyRneOUd3T92kUxuvfY7dLbrBbLd8sLXI-EN4LYO6zOXEBCnoN7MMDWm09eHGkl2P812YFGTSgMqBTWxsyccFcG5MorJ5o4Bu_0qN5l_LvxlQCMHvoEdtBDk99iebli7kIqddii9ZH0pzWBhSTFQjyuw4XUZb338=w311-h432-s-no-gm?authuser=0)

![Dựng Website quản trị](https://lh3.googleusercontent.com/pw/ADCreHeeQpAwZlJA09yuTdSjdHwM7CK7Unp7obLFezOz2h2U_vyBB9xQsQDCqBHAMqAO8t3LIFS0bn_RKbzE37OhKS-J7UTw_TGGX3VKLjpCOFXrr-8kjO4wHGuZgxZJ2mSGmFfZyZXBtJUiRQitOhIt8VacZz8EeNkBeja6OsqmAZZnUOPwmN7yOBlQFIYNKttRhvxlKoC0dXHqIZBn29P7G_2y0zgqRbZA4JP2LrSVVEHtbvQsNvh0_xVCawqxOlKdoz9gP41FFxfrLxDIKqTm-s72OTqXt7S_pJLW6UTGvhsDtWgwoCTB2k970y6hwTpKZgk3tRCQDWr4hN_4ggsx0t6ItcFr3ukfuVPcZgS8vqQgXTzHkd2xWlGHKkKxFytA60PvhpjF9Ik_0Ju5BGUhr4FdReoZpqGuoeSrmTwKU6zwfzN46RXkbVj_6WqZx-VDEQgJE7Az2m1v8y3UtOJTTkVuqudd6RB4U807E08SkhECRDgNCXmYaTjf1rDobigHLdDcTObtoEWxUVwXFsMPPjDfypjcio7PXhoUc2V2HKVdg7Kw56_qCWG2lp84tNqmnRAPHuj8IHPOfUoPE1e5DZ3gNqU4mxiiTxSqGmHYfurmWnHLukWv4Tc5LWAMELubrSwVDk8E-WmCD9cOY1hfy5gdqet4_kycBOGdgQ89447l0mgQzcVqNZpNazT02iDng3N03UJRfMR5aqGChsknJ1Tl3aaFZuO-kwl4Fzk4yMhO07khCoVMg4ebaLKlo3dRhzxAKv9An2p8jHzWWeXg9lVY2_bPt62MDf4CJJCDtWlxk0SaKH46NPrU8y30_4m9135xgEnJi6OUR6asIKpMwWvLMsf6FI9lqG6aHDJx_nY8hmqS9vBq5aJBDERbwtWJZJUYv26bkottuiNH1W1wv4M=w585-h682-s-no-gm?authuser=0)

***Site name:*** Tùy chỉnh

***Physical Path:*** [SVN Path]\Admin\CMS.Admin

***Port:*** Tùy chỉnh

***Application pool:*** pool đã tạo ở trên

Hiệu chỉnh sau khi dựng IIS 

![Hiệu chỉnh sau khi dựng IIS ](https://lh3.googleusercontent.com/pw/ADCreHetz9khmzDU4Sf2k2FtBLhNUX2WJ-ZdwqwiAw9z30nZb-A_dQyTHo9B0UymZimk-mSJCBBY0EX7GrcANAMsQlrj_fi4Y5tXZeWsZhYsXhOazY_AZfCOq77lVQoe1RWRei63uIRUZW7zV4MeW1jZs3EOid3bVeSeIM-30kce2wpiArp0W4Je09ww9wdUM5tXFm6TQu-PpmpphmtyNnSlC_DSylQHy7ZGrf3Jat2xTCJPwjWy556hdF-BL_bb6o4oELTebMzMpNKdQZDV-FouKKtFTFwAaKS_chQ0NLMmncrvsBvw-DeBg6mYtbQ94SJLNEoe7AJ7O-SW6EQfI6DvFoVAuJaZz4rgygD60KztlXK3JjftEiVjuTLvklNU01CLBgEAmuR7xktchrxDZyQx8RAeIBui6e3iotv_1DMfiyfC5u1xvBV6noz4rNPUTl6gaYXL9erU6UijABOsBLVeMmicyrnAJPYc4JK6ws48BqDZ_fI6kQ_V6-86UHWUJDt54IrbEw2dbD7QlBMUY8ZorOz-kIWQMsHcmwb5eje3ruAItprZD-kPwNlD32tWtkXCzLpCSNm68t-g0Fa5QnELdJwVO3e-f1r_ZRktJLdU8PTWYmC7NmCQ9t1RGt81CrnLFMf_s8HmZk5p4_UM-Veto2DsFQYhk5nuA8uN6KiRIxIlKKwP07kt-sxfTHxZ0lBsYXArwJ8PQbMHxlVBkJuSULTBulVmmoRuDJyLBQTKoNt_lkpSqLcYlL1HL8nwxxHaTf0Xkve_3XZoZTdewohJ-w16WYLDNZoq-7m3v68lnZM9fMwfdIcs7XqFYtQo3AJtjbLG-ORq2nUmhvBSHCrl1_KlWCQGYvS6s88ZXZMEvRG6CLNs7QUh0stc4_SQvWjlJqF9xS41aKJQalddlcif_oc=w475-h209-no?authuser=0)

Điều chỉnh port service khai trong **[SVN Path]\Admin\CMS.Admin\Web.config** thành port của service đã dựng ở trên

#### Cách debug

Để debug được chương trình cần mở Visual Studio dưới quyền Administrator và đảm bảo ứng dụng đã chạy được trên IIS và trên trình duyệt
Sử dụng **CTRL + ALT + P** để mở giao diện chọn pool cần debug

![Cách debug ](https://lh3.googleusercontent.com/pw/ADCreHewyrQEJ71iWX-EUA41SpyA9neLKe9d3SzJULYGWWMYscvD1jWeWz8KN_YiFlhWRFAcVt0AUfPDThdGiZkPRAz4MFYo6CEWhuerOHIgsuWYadxmldfzUB9IWBnTLZioHazqZjmILHzlgNCGXsKXfTSrTMer5YyfY3yJScCapnvUKMu1nEesmcxff_KDuY_uvJ2_oyRnleZQH9vRVzn5dWNfecFCMQ4Iz8gUDzrqsPUdcP2HsqXORhI1SjHLi75NoiF99JPp0I-r5iqIyZ-Ji8gF6gX56e2_HrjqD0gcsSg9yW62OMRKjC5sF8fL_l2VgDLjngFC-iHUbx4iI-llGF-X1SXrMtIyFlF0rg3cwuiGqI3NFCnjPXIMWQ7qL6SS354oIW4qKc3mQWumDaGeumNbqhHc_8hlBhOooB7p5fQbaREJqRzhy1b-zNtEKT9S3nxiG2T05oOPm9c4RgOQJVu_ZC6om9eGopaoRH-QogY3GWVs44Js8Ic7HiliJJpFcoElcHeBuXFGu6C14YOq1K5Mg2ZMdIaYVc1NOR6u_9GGzy6Mqy9RptydGO_9XnsPa-KsiiMT-Ewe1Gq0Rau4n1eJppxhkfTN4Wlm6qclXT-1Qy1ZUA6EmusBZtWifjK_bIqqQuR-AR8XNkmjsDU88PtmHtlsh_FIzR3v-48EAGc0SRrsfNzQI_NhiRKg04ShTygS4RJXdoNpU8eGXjgWUKziGrIZAwfbucYKjFKyYu7uRdZKwbaEQI-T0fknTnInDNtmlzFr7XGpsArAvlkAYdq5zzpQXK_w0xB5pjqxDOQyEuWhB2AsQBg_2sKgDDUAMh5-u4BGQauRgR-tskPfmmqjkEEjJqn8hbANMzz4faOToyzzxh6gqYJAarr1I1iO3kpnqFo_r4YD8nG3wft5oGo=w1366-h767-s-no-gm?authuser=0)

Tiến hành debug

#### Cách Lỗi thường gặp

* Dựng sai đường dẫn tới thư mục thự thi ứng dụng

* Visual studio không khởi động với quyền administrator => Lỗi không debug được

* Không cấp quyền user truy cập vào folder Connection chứa chuỗi kết nối databse => Lỗi không kết nối được database

* Contructor Các class khởi tạo lỗi => Lỗi không chạy được services

* Services, Repository chưa đăng ký ở MainModule.cs => Lỗi không chạy được services

* Chưa khai báo Service trong Web.config => Lỗi không chạy được services

* Chưa khai báo Service trong Web.config => Lỗi không chạy được services

* Chưa điều chỉnh port service Web.config => Lỗi website không có dữ liệu

### Website

* Source Website nằm trong thư mục [SVN Path] **( Hỏi teamlead folder cụ thể cho từng đơn vị)**
* Mở solution CMS_Solution.sln trên Visual Studio với quyền Administrator
#### Cấu trúc source

![Cách debug ](https://lh3.googleusercontent.com/pw/ADCreHfZ7pA8JlIpsVFt7bYmhRI0Di8PCcEjEwD9QTSLDOgNeNPnchIXto83gjem5xSzbV4bEvKCP0sS9-vBeOrIMv0BG33FPegwU80QzttE7zxgkjCrNF3gOQshk3WChBDVDhCGGLKbi1bnd-oni3Z7pnQUwu1oQAHJi2kt-hZtMdzbVwEj7c1lEyJW8W7alD5dDzfhUXel_t3Wp7PCMVq4mBlGnDpwM2IzV9xsWRCioMRCJNtCBspcTLrt6qMBdW3M5UFbIN9ym4DYOy20oC-P9Li0dKIItRrdnaCNt1YrF-nHhWIpogNIepxtvhHJIzq9VwHS-kRd9TE9GHTDADzeXNegIrFk6MEb5dJAaHYwTn12Vl7kEm5iWJI9aQOpoUpBygNDEyecc3G8KUcNAo54UlsIAhx7Gf9ihut3zp3RP8J4iZmjACuhc3uQGl7ot51xMHLQSalxT_KwQ09bWXOezOXmND75C94duWKRqhmcIuJUcBMrlBdUSftBDal9QWmuwJWU1kZ_ZVDDGFxQhU8-O1DU0dlffDuDD_gV17VhybKBUpgRU-eyutEnAPigppu_IfnJ5WEoP2daKqqYExbHcGqrajoZ5eImfCt-okMTkZUMxecADwkZntrz9K9SBp-ECAd73ZzWz5V18aHN6uoetlpiiTdEn6bGXsQLvoCRKC3w48SlNXL1BRnqZUA_Qg5M0d2ZvUYAb2VNe8QEaJTnWye-AgOjFMu8Qz7TSHStqArXD9yTAzMEvmH44LPZfdTgIa8PKjWnh6lZBLulhUj7vnZMfn1ir2wxf1CaVOcfx0DJ_ehRZR5fTTyrJwYvO0Sw1kLWG5tBY6tQ0UWMEh-uTcvZE7PKniNezVqEy7FUCzgwIdMquv4PGkOg6p_zfbRFWe9Fj0HPDDJYj4HeggaK3kY=w342-h752-s-no-gm?authuser=0)

#### Cách dựng source

Source chạy trực tiếp

#### Cách debug

Debug trực tiếp

#### Cách Lỗi thường gặp

* Dựng sai đường dẫn tới thư mục thự thi ứng dụng

* Contructor Các class khởi tạo lỗi => Lỗi không chạy được services

* Services, Repository chưa đăng ký ở MainModule.cs => Lỗi không chạy được ứng dụng

### Tool in ấn

* Source Admin nằm trong thư mục [SVN Path]/SocketWindowsService
* Mở solution CMS_Solution.sln trên Visual Studio với quyền Administrator

#### Cấu trúc source

![Cấu trúc source ](https://lh3.googleusercontent.com/pw/ADCreHeghNxy722xC0co_3WzJfQGFTZwY-osbBrWtWpDfNUGG3U2QmtjU3sN8ebLCHzdIKSz67zUMGQ8mWQ5yWu3tK5iz9q-_wwnCX4kLZXmRzl4bZfi9zKnQ45oh7eCBtXGUCJH0aLkPY1maznRo9nTqtMJ9onhpOnwT4lNwqoZPIZMyHZf0aS5UVenLARqTqyK1DLiiD1UK7cMZ0dkR9Z3gBdyE27gJFjYzKDKT4AxBuayXXKdCH5HGEvfSMuIuXZNBPiw1INj5WjYGm2jKrt8vAJDCaaEC79qPud-mL_5DUMCnE4qh1mFDRTMjwdhMR7xGkp6zG_6OToKt9N601EgFUwyt3-0iPEKq7VsSeNijWo4CXaq2wxmtYvK2H8wAm-9IH2EXKiqz6x6JzgFp8xQZNrP5jRwj5LFoYf6EfIEgh5dPUi4MxRlYaJaNszz6OQ7iV0Ihyfq9Pz3BaKZd6oRT5FsUmAKs9oTD_wlJuMkLNAy3ByMQ2BDDwkGD0ls6qhCNvDGdfJ09irF6UVDrvv-kwVm6jLe3GMseka8OBHAj_ZNVEW2hw2Dg1tQxuOktTTPBd3FprLHDTgDViLXk52r7Uz-BiKrB4WEEj_oJo09kKCkuIblHj4OTrmX-041Xa5D8QMbG4WmH0S_ZStpTOJNgrb-vFzO6v_sVTQXTLhbrdZB7t3fuL_5tULJWX8eEH0aiUDslC3x0NfM5-k0DKyfRuMb2TIdg3rOfwhh_bvJqPf5GdGY2MSayZxfRQKDu6i0kyrC6dHTcTK0QyExpjyyzuh_AQMTDzumNuK749ahphyB3wM7XQyMnJd-ng0vMCRcoIrQ_ENR-qSb5PGatUxHhPAV-7DsFDSwO1Qyn76Ce27W3TNGIOMvxubWjeleVzz1RWH5uSBuN5G5zOzifWlSGqM=w326-h71-s-no-gm?authuser=0)

#### Cách deploy
install wsc FPTPrintService trỏ tới đường dẫn thực thi sau khi build tool.

Stop FPTPrintService.

Build file cài đặt **( Mode Release )**.

Cài đặt trực tiếp trên máy thực thi.

Restart FPTPrintService.

