---
title: RDS を返します&quot;ストリームを読み取れません&quot;エラー |Microsoft ドキュメント
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
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3c1c5b3bdb64b61d6a8b8483069701c89c53252
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274051"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS を返します&quot;ストリームを読み取れません&quot;エラー
"ストリーム オブジェクト読み取れなかったため、現在の位置がストリームの末尾か、空です。 空でないストリームの位置プロパティを使用して現在の位置を設定します。 調べるには、ストリームが空のかどうか、Size プロパティを確認します。"  
  
 このエラー メッセージを表示する場合は http 経由でパラメーター化された階層的なクエリを使用した可能性があります。 RDS では、リモートのパラメーター化された階層を使用できません。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)


