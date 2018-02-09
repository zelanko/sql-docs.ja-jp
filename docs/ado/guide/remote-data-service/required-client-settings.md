---
title: "クライアントの設定に必要な |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f542390110169a88b387856ca887a8b3183e01b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="required-client-settings"></a>必要なクライアント設定
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 カスタムを使用する次の設定を指定**DataFactory**ハンドラー。  
  
-   指定"プロバイダー = MS リモート"で、[接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト[プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたは**接続**オブジェクトの接続文字列"**プロバイダー**="キーワード。  
  
-   設定、 [CursorLocation プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**です。  
  
-   使用するハンドラーの名前を指定、 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**ハンドラー**プロパティ、または[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの接続文字列"**ハンドラー**="キーワード。 (で、ハンドラーを設定することはできません、**接続**オブジェクトの接続文字列です)。  
  
 RDS という名前のサーバーで既定のハンドラーを提供する**MSDFMAP です。ハンドラー**です。 (既定値のカスタマイズ ファイルの MSDFMAP を名前です。INI。)  
  
 **例**  
  
 以下のセクションを前提としています。 **MSDFMAP です。INI** AdvWorks、データ ソース名は既に定義されているとします。  
  
```  
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 Visual Basic では、次のコード スニペットが書き込まれます。  
  
## <a name="rdsdatacontrol-version"></a>RDS.DataControl バージョン  
  
```  
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "http://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>レコード セットのバージョン  
  
```  
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 いずれかを指定、[ハンドラー プロパティ (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)プロパティまたはキーワード;、[プロバイダー プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたはキーワード; および*CustomerById*と*CustomerDatabase*識別子。 開き、 **Recordset**オブジェクト  
  
 rs です。"CustomerById(4)"開く"ハンドラー MSDFMAP を = です。_ (&)、ハンドラーです。"  
  
```  
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=http://yourServer"  
```  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイルのセクションを接続します。](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズ ファイル UserList に関するセクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)






















