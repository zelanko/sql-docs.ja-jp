---
title: 非推奨の DBCC CONCURRENCYVIOLATION コマンドの呼び出しを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cde04ebfc2ea9996d1c9ed233123e5b66f6e81fa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065206"
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
  
