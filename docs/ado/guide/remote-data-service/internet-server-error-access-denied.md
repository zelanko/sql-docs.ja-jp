---
title: "インターネット サーバー エラー: アクセスが拒否されました |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0338761d1fbd9991185959cfcac4d54746fb6ebb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="internet-server-error-access-denied"></a>インターネット サーバー エラー: アクセスが拒否されました
このエラーが発生する場合は、通常 Microsoft インターネット インフォメーション サービス (IIS) に次の状態が返されることを意味します。  
  
 HTTP_STATUS_DENIED 401  
  
 IIS がアクセスしているディレクトリが適切な権限を持っていることを確認してください。 RDS が 3 つのパスワードの認証モードのいずれかで実行されている IIS Web サーバーと通信できます。 匿名、Basic、または NT チャレンジ/レスポンス (Windows 2000 で統合 Windows 認証と呼ばれます)。 Web サーバーは、Windows NT または Windows 2000 コンピューターである場合、データ ソースのコンピュータへのアクセス許可が必要です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)





