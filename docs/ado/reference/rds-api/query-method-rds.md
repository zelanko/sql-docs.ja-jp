---
title: "Query メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53647d80b2e6110e5af084e6a3f983381ced1690
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="query-method-rds"></a>クエリ メソッド (RDS)
返す有効な SQL クエリ文字列を使用して、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *レコード セット*  
 オブジェクト変数を表す、 **Recordset**オブジェクト。  
  
 *DataFactory*  
 オブジェクト変数を表す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト。  
  
 *接続*  
 A**文字列**サーバー接続情報を含む値です。 これがに似ていますが、[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティです。  
  
 *Query*  
 A**文字列**SQL クエリを含むです。  
  
## <a name="remarks"></a>解説  
 クエリでは、データベース サーバーの SQL 文法を使用する必要があります。 実行されたクエリでエラーがある場合は、結果のステータスが返されます。 **クエリ**メソッドが、構文のチェックを行わない、**クエリ**文字列。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>参照  
 [DataFactory オブジェクト、クエリのメソッド、および CreateObject メソッドの例 (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)



