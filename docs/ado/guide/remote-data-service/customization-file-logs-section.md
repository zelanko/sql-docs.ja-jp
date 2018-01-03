---
title: "カスタマイズ ファイルのセクションをログに記録 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80f9b0a4d00326d7e9a81554d96b07bbf0817c43
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="customization-file-logs-section"></a>カスタマイズ ファイル ログ
**ログ**セクションには操作中にエラーを記録するファイルの名前を指定するログ ファイルのエントリが含まれています、 **DataFactory**です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
 形式は、ログ ファイルのエントリです。  
  
```  
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>解説  
  
|要素|Description|  
|----------|-----------------|  
|**エラー**|このことを示すリテラル文字列は、ログ ファイル エントリです。|  
|*FileName*|完全なパスとファイル名。 一般的なファイル名が**c:\msdfmap.log**です。|  
  
 ログ ファイルは、ユーザー名、HRESULT、日付、および各エラーの発生時に格納されます。  
  
## <a name="see-also"></a>参照  
 [カスタマイズ ファイルのセクションを接続します。](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズ ファイル SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズ ファイル UserList に関するセクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [カスタマイズ ファイルの概要](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


