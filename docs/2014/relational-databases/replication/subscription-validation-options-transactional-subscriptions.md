---
title: '[サブスクリプションの検証オプション] (トランザクション サブスクリプション) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec241a087a3f82385fef96328b9178e7c15973ee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183429"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>[サブスクリプションの検証オプション]\(トランザクション サブスクリプション)
  **[サブスクリプションの検証オプション]** ダイアログ ボックスを使用すると、検証に行数のみを使用するか、行数とバイナリ チェックサムを使用するかを指定できます。  
  
## <a name="options"></a>および  
 **[サブスクライバーとパブリッシャーでレプリケートされたデータの行数が同じであることを確認します。]**  
 実行する行数の検証の種類を選択します。 Oracle パブリケーションの場合、使用できるオプションは **[テーブルに直接クエリすることにより、実際の行数を計算する]** のみとなります。  
  
 **[行データを比較するためにチェックサムを比較する (この処理には時間がかかります)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。  
  
 **[検証完了後にディストリビューション エージェントを停止する]**  
 既定では、ディストリビューション エージェントは継続的に実行されます。 検証の実行後にエージェントを停止するには、このオプションを選択します。 これにより、サブスクライバーへのデータのレプリケートを継続する前に、検証が成功したかどうかをチェックできます。  
  
## <a name="see-also"></a>参照  
 [サブスクライバーでのデータの検証](validate-data-at-the-subscriber.md)   
 [レプリケートされたデータの検証](validate-replicated-data.md)  
  
  
