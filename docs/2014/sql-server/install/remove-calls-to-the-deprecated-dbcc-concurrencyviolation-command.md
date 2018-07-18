---
title: 非推奨の DBCC CONCURRENCYVIOLATION コマンドへの呼び出しを削除します |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
caps.latest.revision: 7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2486546efae7daa63441e12fa350ef878c7daa77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261898"
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
  
