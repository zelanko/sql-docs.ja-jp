---
title: 非推奨の DBCC CONCURRENCYVIOLATION コマンドへの呼び出しを削除する |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a17b3c844afb6b8b804da258b0330d45dc7208e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164496"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>非推奨の DBCC CONCURRENCYVIOLATION コマンド呼び出しの削除
  アップグレード アドバイザーによって、DBCC CONCURRENCYVIOLATION コマンドの使用が検出されました。 このコマンドは使用できなくなりました。 このコマンドを実行すると、エラー 2526 が返されます。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションの新しいバージョンにはワークロード ガバナーが含まれていないため、コマンドは削除されました。  
  
## <a name="corrective-action"></a>修正措置  
 この非推奨コマンドへの参照を削除するために、アプリケーションおよびスクリプトを更新します。  
  
## <a name="external-resources"></a>外部リソース  
  