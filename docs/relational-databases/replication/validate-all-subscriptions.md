---
title: "[すべてのサブスクリプションの検証] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.validate.allsubscriptions.f1"
helpviewer_keywords: 
  - "[すべてのサブスクリプションの検証] ダイアログ ボックス"
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# [すべてのサブスクリプションの検証]
  使用して、 **すべてのサブスクリプションの検証** ダイアログ ボックスを次回に各サブスクリプションのマージ エージェントが実行する必要があります、マージ パブリケーションに対するすべてのサブスクリプションに検証することを指定します。 検証の結果はレプリケーション モニターに表示されます。 詳しくは、「 [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md)」をご覧ください。  
  
 サブスクリプションを右クリックして、単一のサブスクリプションを検証することも [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をクリックすると、 **サブスクリプションの検証**します。  
  
## オプション  
 **[行数のみを確認する]**  
 選択すると、サブスクライバー側のテーブルとパブリッシャー側のテーブルの行数が同じかどうかを確認できます。 この方法では、行の内容が一致するかどうかは確認されません。 行数の確認は、データに問題があるかどうかを調べる手軽な検証方法です。  
  
 **[行数を確認し、行データを評価するためにチェックサムを比較する (すべてのサブスクライバーは SQL Server 2000 以降を実行しているサーバー)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。 このオプションは [!INCLUDE[ssEW](../../includes/ssew-md.md)] では無効です。  
  
## 参照  
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  