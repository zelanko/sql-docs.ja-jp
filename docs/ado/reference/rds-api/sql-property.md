---
title: SQL プロパティ |Microsoft ドキュメント
ms.technology:
- drivers
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
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 967d1176417a0f8acbdbdfbcea7aad24b804fade
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="sql-property"></a>SQL プロパティ
取得するために使用するクエリ文字列を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
 設定することができます、 **SQL**でデザイン時にプロパティ、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのオブジェクトのタグ、またはスクリプト コードの実行時にします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>パラメーター  
 *QueryString*  
 A**文字列**有効な SQL データ要求を含む値です。  
  
 *DataControl*  
 オブジェクト変数を表す、 **.rds ですDataControl**オブジェクト。  
  
## <a name="remarks"></a>解説  
 一般に、これは、SQL ステートメント (データベース サーバーの言語を使用) など`"Select * from NewTitles"`です。 レコードが一致しを正確に更新されるようにするには、更新可能なクエリは、バイナリ長フィールドまたは計算フィールド以外のフィールドを含める必要があります。  
  
 **SQL**プロパティはオプションの場合は、サーバー側のカスタム ビジネス オブジェクトは、クライアントのデータを取得します。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [SQL プロパティの例 (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [プロパティ (RDS) 接続します。](../../../ado/reference/rds-api/connect-property-rds.md)   
 [クエリ メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


