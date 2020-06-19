---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9a79169e18ec7c84056b5fd5cb1ae666e7b39c7e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969532"
---
# <a name="mssqlserver_15517"></a>MSSQLSERVER_15517
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|15517|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_CANNOTEXECUTEASUSER|  
|メッセージ テキスト|データベース プリンシパルとして実行できません。プリンシパル "*principal*" が存在しないか、この種類のプリンシパルで権限を借用できないか、ユーザーに権限がありません。|  
  
## <a name="user-action"></a>ユーザーの操作  
 既存のプリンシパルの名前を使用するか、そのプリンシパルに対する IMPERSONATE 権限を取得します。  
  
 15517 は、元のデータベースの所有者以外のユーザーによってデータベースのアタッチおよび復元が実行された後に発生する可能性があります。 このエラーを解決するには、次のコマンドを実行して、サーバーにログインするための db_owner を変更します。  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
