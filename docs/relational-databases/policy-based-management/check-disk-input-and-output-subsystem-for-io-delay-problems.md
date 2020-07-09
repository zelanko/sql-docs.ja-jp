---
title: ディスク IO サブシステムの IO 遅延の問題の確認
description: SQL Server によるポリシーベース管理のエラー メッセージ 833 がないか、イベント ログを確認することで、ディスク IO サブシステムの IO 遅延問題を確認するためのポリシーを有効にする方法について説明します。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f8c880438491f697d57134b5004129eef38a7fe8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749509"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a>ディスク I/O サブシステムの I/O 遅延問題の確認
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このルールでは、イベント ログのエラー メッセージ 833 を確認します。 このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからの読み取り要求やディスクへの書き込み要求を発行してからその要求が完了するまでの時間が 15 秒を超えたことを示しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からこのエラーが報告された場合は、ディスク I/O サブシステムに問題があります。 この長い遅延が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境のパフォーマンスに深刻な悪影響を及ぼす可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 このエラーのトラブルシューティングを行うには、システム イベント ログを参照し、ハードウェア関連のエラー メッセージが記録されているかどうかを調べます。 また、可能な場合はハードウェア固有のログも調べます。  
  
 パフォーマンス モニターを使用して、次のカウンターを調べます。  
  
-   Avg. Disk sec/Transfer  
  
-   Avg. Disk Queue Length  
  
-   Current Disk Queue Length  
  
 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの Avg. Disk sec/Transfer の時間は、通常 15 ミリ秒未満です。 Avg. Disk sec/Transfer の値が増加している場合、ディスク I/O サブシステムが I/O 要求を最適な速度で処理できていません。  
  
## <a name="for-more-information"></a>詳細情報  
   
  
 [サポート技術情報の資料 897284](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 [SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))
