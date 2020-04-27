---
title: '[すべてのサブスクリプションの検証] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b33cfe47cebba4c24c90ad41ce1b218192d128f4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63255324"
---
# <a name="validate-all-subscriptions"></a>[すべてのサブスクリプションの検証]
  **[すべてのサブスクリプションの検証]** ダイアログ ボックスを使用すると、各サブスクリプションのマージ エージェントを次に実行するときに、マージ パブリケーションへのサブスクリプションをすべて検証するように指定できます。 検証の結果はレプリケーション モニターに表示されます。 詳しくは、「 [Validate Data at the Subscriber](validate-data-at-the-subscriber.md)」をご覧ください。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクリプションを右クリックし、 **[サブスクリプションの検証]** をクリックすることでも、1 つのサブスクリプションを検証することができます。  
  
## <a name="options"></a>オプション  
 **[行数のみを確認する]**  
 選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。 この方法では、行の内容が一致するかどうかは確認されません。 行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。  
  
 **[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。 このオプションは [!INCLUDE[ssEW](../../includes/ssew-md.md)]では無効です。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータの検証](validate-data-at-the-subscriber.md)  
  
  
