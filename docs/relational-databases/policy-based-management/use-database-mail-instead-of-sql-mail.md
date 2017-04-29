---
title: "SQL Mail ではなくデータベース メールを使用する | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81e3e1ee2e090e7c87ad910430846be372f9267e
ms.lasthandoff: 04/11/2017

---
# <a name="use-database-mail-instead-of-sql-mail"></a>SQL Mail ではなくデータベース メールを使用する
  このルールでは、sys.configurations カタログ ビューを確認して、サーバー全体に適用される構成オプションである SQL Mail XPs が ON に設定されているかどうかを調べます。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 SQL Mail は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンで削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 メールを送信するには、データベース メールを使用してください。  
  
 SQL Mail は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対してインプロセスで実行されます。 SQL Mail がダウンした場合、サーバーもダウンします。 データベース メールは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部の別個のプロセスで実行され、スケーラブルです。拡張 MAPI クライアント コンポーネントを実稼働サーバーにインストールする必要はありません。  
  
## <a name="for-more-information"></a>詳細情報  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
