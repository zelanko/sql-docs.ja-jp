---
title: カスタマイズ ファイルの概要 |Microsoft ドキュメント
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
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a80667371709c4035a4a45fa4e322d59f03f5bc7
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274581"
---
# <a name="understanding-the-customization-file"></a>カスタマイズ ファイルの概要
カスタマイズ ファイルの各セクション ヘッダーは、角かっこで構成されます (**[]**) 型とパラメーターを格納します。 次の 4 つのセクションの種類は、リテラル文字列で示されます。**connect**、 **sql**、 **userlist**、または**logs**です。 パラメーターでは、リテラル文字列、既定値、ユーザー指定の識別子では、または何も行われません。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 したがって、各セクションでは、次のセクション ヘッダーのいずれかのマークされました。  
  
```  
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 セクション ヘッダーには、次の一部が含まれています。  
  
|要素|説明|  
|----------|-----------------|  
|**connect**|接続文字列を変更するリテラル文字列。|  
|**sql**|コマンド文字列を変更するリテラル文字列。|  
|**userlist**|特定のユーザーのアクセス権を変更するリテラル文字列。|  
|**logs**|操作エラーを記録するログ ファイルを指定するリテラル文字列。|  
|**default**|識別子のないを指定または検索された場合に使用されるリテラル文字列。|  
|*identifier*|文字列に一致する文字列、**接続**または**コマンド**文字列。<br /><br /> セクションを使用してこのセクションのヘッダーが含まれている場合**connect**接続文字列で、識別子の文字列があるとします。<br />セクションを使用してこのセクションのヘッダーが含まれている場合**sql**コマンド文字列内に識別子の文字列があるとします。<br />セクションを使用してこのセクションのヘッダーが含まれている場合**userlist**識別子文字列と一致して、**connect**セクションの識別子。|  
  
 **DataFactory**クライアント パラメーターを渡すこと、ハンドラーを呼び出します。 ハンドラーは、該当するセクション ヘッダー内の識別子に一致するクライアント パラメーターで全体の文字列を検索します。 一致が見つかった場合、そのセクションの内容は、クライアント パラメーターに適用されます。  
  
 特定のセクションは、次の状況で使用されます。  
  
-   **connect** セクションは、クライアントの値部分文字列のキーワードを接続する場合は、使用 "**Data Source =***value*"、一致する、**connect** セクション識別子 *。*  
  
-   **Sql** セクションには、クライアントのコマンド文字列に一致する文字列が含まれている場合、使用、 **sql** セクションの識別子。   
  
-   **connect**または**sql**既定パラメーターを持つセクションは、一致する識別子が存在しない場合に使用します。  
  
-   **userlist** セクションは場合、使用、 **userlist** 識別子と一致するセクション、**connect** セクションの識別子。 内容、一致がある場合、 **userlist** セクションは、制約を受ける接続に適用されます、**connect** セクションです。  
  
-   接続またはコマンド文字列内の文字列がいずれかで識別子と一致しない場合**connect** または**sql** セクションのヘッダー、およびがない**connect** または**sql** 変更せずに、クライアントの文字列を使用し、既定のパラメーターを持つヘッダーをセクションです。  
  
-   **logs** セクションは、使用されるたびに、 **DataFactory** の操作ができます。  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイル Connect セクション](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル Logs セクション](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズ ファイル SQL セクション](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズ ファイル UserList セクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)




















