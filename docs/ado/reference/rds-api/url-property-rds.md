---
title: URL プロパティ (RDS) |Microsoft ドキュメント
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e798b7e4afd6ddf0e2238acff56adcff0a3cfb5c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="url-property-rds"></a>URL プロパティ (RDS)
相対パスまたは絶対 URL を含む文字列を示します。  
  
 設定することができます、 **URL**でデザイン時にプロパティ、 [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのタグ、または実行時にコードをスクリプトでします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>パラメーター  
 *[サーバー]*  
 A**文字列**有効な URL を含む値です。  
  
 *DataControl*  
 オブジェクト変数を表す、 **DataControl**オブジェクト。  
  
## <a name="remarks"></a>解説  
 通常、URL は特定生成したり、返すできる Active Server Page (.asp) ファイル、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 このため、ユーザーを取得できます、**レコード セット**をサーバー側を呼び出すことがなく[DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト、またはカスタムのビジネス オブジェクトをプログラミングします。  
  
 場合、 **URL**プロパティが設定されている、 [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) URL で指定された場所への変更を送信します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [URL プロパティの例 (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


