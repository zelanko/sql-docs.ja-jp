---
title: カスタマイズ ファイルのセクションの接続 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6774d32587a2c6d5c969be4d56640d137972ddc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273851"
---
# <a name="customization-file-connect-section"></a>カスタマイズ ファイルのセクションを接続します。
ハンドラーの既定の動作は、すべての接続を拒否するのにです。 **接続**セクションでは、その動作に例外を指定します。 たとえば、すべての場合、**接続**セクションがないか、空で、既定で接続を確立できませんでした。  
  
 **接続**セクションに含めることができます。  
  
-   既定値を指定する既定のアクセス エントリは、この接続で許可される操作を読み書きします。 セクション内に既定のアクセス エントリがない場合は、セクションは無視されます。  
  
-   クライアントの接続文字列を置換する新しい接続文字列。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 形式は、既定のアクセス エントリです。  
  
```  
  
Access=  
accessRight  
  
```  
  
 形式は、接続文字列の置換エントリです。  
  
```  
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>コメント  
  
|要素|説明|  
|----------|-----------------|  
|**のインスタンスに接続するときには、**|このことを示すリテラル文字列は、接続文字列エントリです。|  
|***connectionString***|全体のクライアントの接続文字列を置換する文字列。|  
|**アクセス**|このことを示すリテラル文字列は、アクセス エントリです。|  
|***accessRight***|次のアクセス権のいずれか。<br /><br /> -   **NoAccess** -ユーザーがデータ ソースにアクセスできません。<br />-   **読み取り専用**-ユーザーは、データ ソースを読み取ることができます。<br />-   **ReadWrite** : ユーザーの読み取りまたはデータ ソースに書き込むことができます。|  
  
 (影響、既定のハンドラーの動作を無効にする) に任意の接続を許可する場合でアクセス エントリを設定、**接続既定**セクション`Access=ReadWrite`、削除したり、コメント アウト、他の**接続***識別子*セクションです。  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイル ログ](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズ ファイル SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズ ファイル UserList に関するセクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



