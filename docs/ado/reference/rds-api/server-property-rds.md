---
title: "サーバー プロパティ (RDS) |Microsoft ドキュメント"
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RDS::IBindMgr21::Server
helpviewer_keywords:
- Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a81a3139892898b8468d73f53d22d8bd29c4b63
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="server-property-rds"></a>サーバー プロパティ (RDS)
インターネット インフォメーション サービス (IIS) の名前との通信プロトコルを示します。  
  
 設定することができます、**サーバー**の OBJECT タグには、デザイン時プロパティ、[.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト、または実行時にコードをスクリプトでします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 **HTTP**  
  
 デザイン時の構文  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 実行時の構文  
  
```  
  
DataControl  
.Server="http://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 デザイン時の構文  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 実行時の構文  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 デザイン時の構文  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 実行時の構文  
  
```  
  
DataControl.Server="computername"  
```  
  
 **処理中**  
  
 デザイン時の構文  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 実行時の構文  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>パラメーター  
 *awebsrvr*または*computername*  
 A**文字列**サーバーが、ローカル コンピューター上にある場合に、サーバーがリモート コンピューターです。 または、空の文字列がある場合は、インターネットまたはイントラネット パス、またはコンピューター名を含む値です。  
  
 *port*  
 省略可。 IIS を実行しているサーバーに接続するために使用するポートです。 Internet Explorer で、ポート番号を設定 (上、**ビュー**  メニューのをクリックして**オプション**、し、選択、**接続** タブ) または IIS でします。  
  
 *DataControl*  
 オブジェクト変数を表す、 **.rds ですDataControl**オブジェクト。  
  
## <a name="remarks"></a>解説  
 サーバーの場所は、ここで、 **.rds ですDataControl** (つまり、クエリまたは更新) の要求を処理します。 によって既定では、すべての要求の処理、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト、 [MSDFMAP です。ハンドラー](../../../ado/guide/remote-data-service/datafactory-customization.md)コンポーネント、および[MSDFMAP です。INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)指定されたサーバー上のファイルです。 古いマスター_キーと新しい設定を調整するためにサーバーを変更する場合の点に注意**MSDFMAP です。INI**ファイル。 非互換性が別の失敗の 1 つのサーバーで成功した要求があります。 サーバー プロパティが空の文字列に設定されている場合""、これらのオブジェクトがローカル コンピューターに適用されます。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [サーバー プロパティの例 (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [プロパティ (RDS) 接続します。](../../../ado/reference/rds-api/connect-property-rds.md)   
 [SQL プロパティ](../../../ado/reference/rds-api/sql-property.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


