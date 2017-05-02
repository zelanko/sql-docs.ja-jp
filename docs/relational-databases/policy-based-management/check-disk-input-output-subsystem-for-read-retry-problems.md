---
title: "ディスク I/O サブシステムの読み取り再試行の問題の確認 | Microsoft Docs"
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
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c40f4c7e64d8ee022618c2d5d6bc962b1a94b398
ms.lasthandoff: 04/11/2017

---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>ディスク I/O サブシステムの読み取り再試行の問題の確認
  このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベント ログにエラー メッセージ 825 があるどうかを確認します。 このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最初の試行ではディスクからデータを読み取れなかったことを示します。 このメッセージは、ディスク I/O サブシステムに大きな問題があることを示しています。 このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、 ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 次の操作を行って、原因となっているハードウェアの問題を特定し、解決してください。  
  
-   このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。  
  
-   ディスク システムを確認する。 この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。  
  
-   ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。  
  
-   ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。  
  
## <a name="for-more-information"></a>詳細情報  
 [MSSQLSERVER_825](http://msdn.microsoft.com/library/f69f8214-5af1-4769-878b-117ad6eaff52)  
  
 [SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
