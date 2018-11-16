---
title: 'インターネット サーバー エラー: アクセスが拒否されました |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b7c562e57341dd027a4cd9bdc3a0fa4bbe51ae5
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558399"
---
# <a name="internet-server-error-access-denied"></a>インターネット サーバー エラー: アクセス拒否
このエラーが発生する場合は、通常、Microsoft インターネット インフォメーション サービス (IIS) で、次の状態が返されることを意味します。  
  
 HTTP_STATUS_DENIED 401  
  
 IIS がアクセスしているディレクトリが適切な権限を持っていることを確認します。 RDS は、次の 3 つのパスワード認証モードのいずれかで実行されている IIS Web サーバーと通信できる: Anonymous、Basic、または NT チャレンジ/レスポンス (Windows 2000 では統合 Windows 認証と呼ばれます)。 また、Web サーバーは、Windows NT または Windows 2000 コンピューターである場合、データ ソースのコンピューターへのアクセス許可が必要です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)




