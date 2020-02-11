---
title: 必要なクライアント設定 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bdb99cb3d792900f48ceb69c25c7ae720c339683
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922293"
---
# <a name="required-client-settings"></a>必要なクライアントの設定
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 カスタム**DataFactory**ハンドラーを使用するには、次の設定を指定します。  
  
-   [接続オブジェクト (ado)](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト[プロバイダープロパティ (ado)](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたは**接続**オブジェクト接続文字列 "**Provider**=" キーワードで、"provider = MS Remote" を指定します。  
  
-   [[カーソルの場所] プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**に設定します。  
  
-   [DataControl object (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの**ハンドラー**プロパティ、または[レコードセットオブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの接続文字列 "**handler**=" キーワードで使用するハンドラーの名前を指定します。 (**接続**オブジェクトの接続文字列でハンドラーを設定することはできません)。  
  
 RDS では、Msdfmap という名前のサーバーに既定のハンドラーが用意されて**います。ハンドラー**。 (既定のカスタマイズファイルは、MSDFMAP という名前です。INI)  
  
 **例**  
  
 ここでは、Msdfmap の次のセクションについて説明し**ます。INI**とデータソース名た advworks-srv01 が既に定義されています。  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 次のコードスニペットは Visual Basic で記述されています。  
  
## <a name="rdsdatacontrol-version"></a>RDS.DataControl のバージョン  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>レコードセットのバージョン  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 [ハンドラプロパティ (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)プロパティまたはキーワードを指定します。[Provider プロパティ (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)プロパティまたはキーワードおよび*CustomerById*と*顧客のデータベース*識別子。 次に、**レコードセット**オブジェクトを開きます。  
  
 cmr."CustomerById (4)", "Handler = MSDFMAP" を開きます。ハンドラ; "& _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>参照  
 [カスタマイズファイルの接続セクション](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズファイル SQL セクション](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズファイルの UserList セクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズファイルについて](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

