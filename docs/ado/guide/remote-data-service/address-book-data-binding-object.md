---
title: "アドレス帳のデータ バインディング オブジェクト |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 644180448474d2c07b1f53b570e25ac39074edfb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="address-book-data-binding-object"></a>アドレス帳のデータ バインディング オブジェクト
アドレス帳を使用して、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)クライアント HTML ページで、アプリケーションの SQL Server データベースからデータを (この場合は、DHTML テーブル) 内のビジュアル オブジェクトにバインドするオブジェクト。 VBScript プログラム イベント ドリブン ロジックを使用して、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)に。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
-   データベースを照会し、更新プログラムをデータベースに送信データ グリッドを更新します。  
  
-   データ グリッドに前に、次に、最初に移動または最後のレコードにユーザーを許可します。  
  
 次のコード定義、 **.rds ですDataControl**コンポーネント。  
  
```  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 OBJECT タグを定義、 **.rds ですDataControl**コンポーネントをプログラムでします。 タグには、2 種類パラメーターにはが含まれています。  
  
-   ジェネリックの OBJECT タグに関連付けられているものとします。  
  
-   固有のもの、 **.rds ですDataControl**オブジェクト。  
  
## <a name="generic-object-tag-parameters"></a>汎用オブジェクト タグ パラメーター  
 次の表では、OBJECT タグに関連付けられているパラメーターについて説明します。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|***CLASSID***|システムに埋め込まれたオブジェクトの種類を識別する一意な 128 ビットの数。 この識別子は、ローカル コンピューターのシステム レジストリに保持されます。 (のクラス id、 **.rds ですDataControl**オブジェクトを参照してください[.rds ですDataControl オブジェクト](../../../ado/reference/rds-api/datacontrol-object-rds.md))。|  
|***ID***|コードでの識別に使用される埋め込みオブジェクトのドキュメント全体にわたる識別子を定義します。|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS.DataControl タグのパラメーター  
 次の表に固有のパラメーター、 **.rds ですDataControl**オブジェクト。 (の完全な一覧については、 **.rds ですDataControl**オブジェクト パラメーターとすると、それらを実装しを参照してください[.rds ですDataControl オブジェクト](../../../ado/reference/rds-api/datacontrol-object-rds.md))。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|[サーバー](../../../ado/reference/rds-api/server-property-rds.md)|HTTP を使用している場合、値が続く、サーバー コンピューターの名前は`http://`します。|  
|[接続](../../../ado/reference/rds-api/connect-property-rds.md)|接続に必要な情報を提供、 **.rds ですDataControl** SQL Server に接続します。|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|設定または取得するために使用するクエリ文字列を返します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。|  
  
## <a name="see-also"></a>参照  
 [アドレス帳のコマンド ボタン](../../../ado/guide/remote-data-service/address-book-command-buttons.md)



