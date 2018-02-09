---
title: "カスタマイズ ファイルの SQL セクション |Microsoft ドキュメント"
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
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06b3a79e97c50df8c7eed17b1343030ca2280426
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="customization-file-sql-section"></a>カスタマイズ ファイル SQL
**Sql**セクションでは、クライアントのコマンド文字列を置換する新しい SQL 文字列を含めることができます。 セクションでは、SQL 文字列がない、セクションは無視されます。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 新しい SQL 文字列がある*パラメーター化された*です。 内のパラメーターは、 **sql** SQL 文字列のセクション (によって指定された、'?' 文字) に対応する引数に置き換えることができます、*識別子*クライアントのコマンド文字列に (によって指定された、コンマ区切りリストをかっこで)。 識別子と引数のリストは、関数呼び出しと同様に動作します。  
  
 たとえば、クライアントのコマンド文字列は`"CustomerByID(4)"`、SQL セクション ヘッダーが`[SQL CustomerByID]`、および新しい SQL セクション文字列が`"SELECT * FROM Customers WHERE CustomerID = ?".`、ハンドラーが生成されます`"SELECT * FROM Customers WHERE CustomerID = 4"`を使用してその文字列をデータ ソースをクエリします。  
  
 新しい SQL ステートメントが、null 文字列である場合 ("")、セクションは無視されます。  
  
 新しい SQL ステートメントの文字列が有効でない場合は、ステートメントの実行は失敗します。 クライアント パラメーターは無視されます。 意図的にオフにする""クライアントのすべての SQL コマンドを指定してこれを行うことができます。  
  
```  
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>構文  
 形式は、置換 SQL 文字列を入力します。  
  
 **SQL=**   
 ***sqlString***  
  
|要素|Description|  
|----------|-----------------|  
|**SQL**|このことを示すリテラル文字列は、SQL セクション エントリです。|  
|***sqlString***|クライアントの文字列を置換する SQL 文字列です。|  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイルのセクションを接続します。](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル ログ](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズ ファイル UserList に関するセクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


