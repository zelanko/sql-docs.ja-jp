---
title: RDS 返します&quot;未読の Stream&quot;エラー |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc2944e213e2a6a8ba3f9dc51a9a23b496f4e31a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613920"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS 返します&quot;未読の Stream&quot;エラー
"Stream オブジェクト読み取れなかったため、現在の位置が、Stream の末尾か、空です。 空でないストリームで位置プロパティを使用して現在の位置を設定します。 調べるには、Stream が空のかどうか、Size プロパティを確認します。"  
  
 このエラー メッセージを表示する場合は http 経由でパラメーター化された階層のクエリを使用した可能性があります。 RDS では、リモートのパラメーター化された階層を使用できません。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)


